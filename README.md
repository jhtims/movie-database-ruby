# movie-database-ruby
A prototype movie database program to add, update, display, and delete movies and ratings using Ruby.

movies = {Every_Which_Way_But_Loose: 10,
iRobot: 7
}

puts "Welcome to my Movie Review Database 1.0!"
puts "MAIN MENU"
puts "-- Type 'add' to add a movie."
puts "-- Type 'update' to update a movie's rating you've already added."
puts "-- Type 'display' to display all movies."
puts "-- Type 'delete' to delete a movie."

choice = gets.chomp.downcase

case choice
when "add"
    puts "Add a movie title:"
    title = gets.chomp
    if movies[title.to_sym].nil?
        puts "Rate this movie from 1-10:"
        rating = gets.chomp
        movies[title.to_sym] = rating.to_i
        puts "#{title} was added and rated #{rating} out of 10."
    else
        puts "#{title} is already in your database!"
    end
when "update"
    puts "Enter the movie title you want to edit:"
    title = gets.chomp
    if movies[title.to_sym].nil?
        puts "This movie isn't in your database."
    else
        puts "Enter a new rating from 1-10."
        rating = gets.chomp
        movies[title.to_sym] = rating.to_i
        puts "#{title} was edited and rated #{rating} out of 10."
    end
when "display"
    movies.each {|movie, rating| puts "#{movie}: #{rating}"}
when "delete"
    puts "Enter the title you want deleted:"
    title = gets.chomp
    if movies[title.to_sym].nil?
        puts "This movie isn't in your database."
    else
        movies.delete(title)
        puts "#{title} was deleted!"
    end
else
    puts "Error!"
end

