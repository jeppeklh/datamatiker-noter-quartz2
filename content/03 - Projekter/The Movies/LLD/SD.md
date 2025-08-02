## Iteration 1
Baseret på [[Usecase#Use Case Tilføjelse af film|Usecase: Tilføjelse af film]]
DCD: [[DCD#Iteration 1|TheMovies DCD]]

```plantuml
@startuml  
-> MainWindow : Add Movie  
MainWindow -> MainViewModel : AddMovie()  
MainViewModel --> Movie : Create(Movie)  
alt if valid input  
MainViewModel -> MovieRepo : AddMovie(Movie)  
end  
MovieRepo --> MainViewModel : movies : List<Movie>  
loop foreach Movie movie in movies  
MainViewModel -> MovieViewModel : Convert movie to movieVM  
MovieViewModel --> MainViewModel : Add movieVM to movieVMs (ObservableCollection)  
end  
loop foreach MovieViewModel movieVM in movieVMs  
MainViewModel --> MainWindow : Bind ViewModels to ListBox  
end  
@enduml
```

---

## Iteration 2
Baseret på [[Usecase#Use Case 2 Tilføje ny forestilling|Usecase: Tilføj ny forestilling]]

```plantuml
@startuml

-> MainWindow : Add Showing

MainWindow -> ShowingPageViewModel : GoToSHowingPage()

MovieRepo --> ShowingPageViewModel : movies : List<Movie>  
CinemaRepo --> ShowingPageViewModel : cinemas : List<Cinema>

loop foreach Movie movie in movies  
ShowingPageViewModel -> MovieViewModel : Convert movie to movieVM  
MovieViewModel --> ShowingPageViewModel : Add movieVM to movieVMs (ObservableCollection)  
end

alt if valid input  
ShowingPageViewModel --> Showing : Create(Showing)  
MainViewModel -> ShowingRepo : AddShowing(Showing)  
end

ShowingRepo --> MainViewModel : showings : List<Showing>

Loop foreach Showing showing in showings  
MainViewModel -> ShowingViewModel : Convert showing to showingVM  
ShowingViewModel --> MainViewModel : Add showingVM to showingVMs (ObservableCollection)  
end

loop foreach ShowingViewModel showingVM in showingVMs  
MainViewModel --> MainWindow : Bind ViewModels to DataGrid  
end

@enduml
```


