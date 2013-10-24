class MoviesController < ApplicationController

  def show
    id = params[:id] # retrieve movie ID from URI route
    @movie = Movie.find(id) # look up movie by unique ID
    # will render app/views/movies/show.<extension> by default
  end

  def index
	@all_ratings = Movie.uniq.pluck(:rating)

	if(params[:sort] == "title")
          @movies = Movie.order('title ASC')
          @highlight = "title"
	elsif(params[:sort] == "date")
          @movies = Movie.order('release_date DESC')
          @highlight = "date"
        elsif(params[:ratings])
	@ratingSet = Array.new
	@ratings = params[:ratings]
	@ratings.each_key{|key|
		key = key.to_s
	@ratingSet.push(key)}
		@movies = Movie.where(rating: [@ratingSet])
	else
          @movies = Movie.all   
        end

      
  
      end

  def new
    # default: render 'new' template
  end

  def create
    @movie = Movie.create!(params[:movie])
    flash[:notice] = "#{@movie.title} was successfully created."
    redirect_to movies_path
  end

  def edit
    @movie = Movie.find params[:id]
  end

  def update
    @movie = Movie.find params[:id]
    @movie.update_attributes!(params[:movie])
    flash[:notice] = "#{@movie.title} was successfully updated."
    redirect_to movie_path(@movie)
  end

  def destroy
    @movie = Movie.find(params[:id])
    @movie.destroy
    flash[:notice] = "Movie '#{@movie.title}' deleted."
    redirect_to movies_path
  end
 

end
