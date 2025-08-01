

**Hvad er fordelene ved at logge IP-adresse ved loginforsøg?**

- Gør det muligt at opdage geografisk mistænkelige mønstre.
     
- Bruges til at blokere bestemte IP'er.
    
- Hjælper med retslig efterforskning eller support.
    





**Hvordan kunne systemet udvides til at sende advarsler ved gentagne fejlforsøg?**  
Man kunne:

- Tilføje e-mail/SMS-varslinger til administratorer.
    
- Bruger SignalR til realtidsnotifikationer.
    
- Integrere med f.eks. Discord eller Slack via webhook.
    

---


```plantuml
@startuml
title Log and handle Login Attempts

actor User
participant "Login.razor\n(@code + UI)" as LoginForm
participant "SignInManager" as SignIn
participant "DbContext" as Db
participant "ILogger<Login>" as Logger
participant "RedirectManager" as Redirect
participant "LoginAttempt\n(Model)" as AttemptModel

== User submits login form ==

User -> LoginForm : Fills out Email and Password
activate LoginForm

alt if Formular is valid
    LoginForm -> LoginForm : LoginUser()
    
      == Check for existing lockout ==
    
    LoginForm -> SignIn : IsLockedOutAsync(email)
    activate SignIn
    SignIn --> LoginForm : true / false
    alt if User is locked out
        LoginForm -> Redirect : RedirectTo("Lockout")
        activate Redirect
    end

== Attempt login ==

    LoginForm -> SignIn : PasswordSignInAsync(...)
    SignIn --> LoginForm : SignInResult

 == Log login attempt ==

    LoginForm --> AttemptModel : <<create>> LoginAttempt
    activate AttemptModel
    deactivate AttemptModel
    
    LoginForm -> Db : Add(LoginAttempt)
    activate Db
    LoginForm -> Db : SaveChangesAsync()
    deactivate Db

== Handle result of login ==

    alt If SignInResult succesful
        LoginForm -> Logger : LogInformation(...)
        activate Logger
        LoginForm -> Redirect : RedirectTo(ReturnUrl)
        
        note right of LoginForm
          Redirects to originally requested page.
          Example: /admindashboard
        end note
        
    else Else Needs 2FA
        LoginForm -> Logger : LogInformation(...)
        LoginForm -> Redirect : RedirectTo("LoginWith2FA")
    else Else User is locked out
        LoginForm -> SignIn : GetLockoutEndDateAsync()
        deactivate SignIn
        LoginForm -> Logger : LogWarning(...)
        LoginForm -> Redirect : RedirectTo("Lockout")
        deactivate Redirect
    else Else Error in login
        LoginForm -> Logger : LogWarning(...)
        deactivate Logger
        LoginForm --> User : Show error message
    end
    
    
== Validation failed ==

else Else Formular is invalid
    LoginForm --> User : Show validation error
    deactivate LoginForm
end

@enduml
```

```plantuml
@startuml
title Show login attempts in Admin Dashboard

actor Admin
participant "AdminDashboard.razor" as Dashboard
participant "ApplicationDbContext" as Db
participant "ILogger<AdminDashboard>" as Logger

== Admin opens dashboard ==

Admin -> Dashboard : Page load / OnInitializedAsync()
activate Dashboard

Dashboard -> Db : Query LoginAttempts (last hour)
activate Db
Db --> Dashboard : List<LoginAttempt>

Dashboard -> Dashboard : Group by User
Dashboard --> Admin : Shows updated list of LoginAttempts


== Admin filters or searches ==

Admin -> Dashboard : Chooses filter / Writes Email
Dashboard -> Db : Query LoginAttempts (with filters)
Db --> Dashboard : Filtered List<LoginAttempt>
deactivate Db

alt Error in query
    Dashboard -> Logger : LogError(...)
    activate Logger
    deactivate Logger
end

Dashboard --> Admin : Shows filtered list of LoginAttempts
deactivate Dashboard
@enduml
```
