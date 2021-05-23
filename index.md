# Preface
[frequentcolors.com](frequentcolors.com)

The Frequent Colors project is a website that fetches random album covers from the internet and analyzes them. Each album cover or image is looped through pixel by pixel to find the most frequent color in it. This color, with its corresponding album cover is displayed on the website. The color is also added to a database that keeps track of this information and displays some of it on the website. As of now, the website and information gathered has no real purpose, it is just a fun way to display different colors.

I started the Frequent Colors project because I was bored and I wanted a sort of art project to do. I'm not very good at most forms of art, so I tried to think of something I could do to blend art with something I am good at - coding. I really like color and creating new colors with hex codes, so I decided to do something with color. I explored many ideas, including using the [Archillect API](https://archillect.com/api) to source random images for this project. However, I settled on music cover albums because I also love music.

**New images are not currently being fetched, but the website is still up for viewing. If the "Images Processed" Section isn't working (or any other section) just refresh the page and it should work**

# Coding
The first step in this project was fetching images to analyze. Finding an API or a method to fetch thousands of random images from the internet is much easier than it sounds. Luckily, the [MusicBrainz API](https://musicbrainz.org/doc/MusicBrainz_API) allows me to do just that, with music album covers. This API combined with a list of thousands of artists, allowed me to search and fetch thousands of album covers. I implemented a sleep period after fetching an image so that my site wouldn't overwhelm the API.

The next step was to analyze the colors of the image we fetched. I did this in python, after also fetching the image in python. It is quite easy to loop over every pixel and get color data using [Pillow Package](https://pillow.readthedocs.io/en/stable/). I stored the color and count of each color in a dictionary. Once I was done looping over the pixels, I could sort the dictionary by value and get the most common color in the image.

So now that I had the most frequent color, I had to display it on the website and store that information. I did this using a SQL database. I actually used 2: one to keep track of how many times a color was the most frequent and another one to keep track of just the last image we processed. This second database made it easy to get this data using PHP and display it on my website. So, I then pushed the data from python onto the SQL databases. 

Now that the information was in the database, I used PHP to query the database and display it on the website. I also used CSS to help style the website and basic HTML for the rest of the website. To display the current album cover that I was analyzing, I saved the image that I retrieved with python to the same folder that my website was saved.

I then bought some server space and a domain, and I SFTPed all my files onto the server to post the website to the internet.

Unfortunately, my code has some sensitive information (API keys, emails), so it is store in a private repository that I can't share.

# Conclusion
I came into the project with just some basic HTML knowledge and I had to learn a lot. The hardest thing for me was the PHP code and the SQL database because I had never worked with them in the past. There was a lot of research that I did to find the best way to communicate between Python code and my website. I'm not sure I had the best approach to this, but it worked for me. However, it did not come easy. There was a lot of trial and error and debugging that I had to do just to get very basic things to work. I think it is interesting to see how much work goes into creating a website that is perceived as very basic by anyone viewing it. I respect web design and all the effort to make user-facing interfaces simple and clean.

I ran into a few issues in my website that I stil have not been able to fix. One of my ideas for the site was to have a section to display a random color in my database. So I wanted to generate a random number **i** and display the **i**th most frequent color. The SQL queries began to get complicated and I couldn't find a good way to generate a random number. I think the best approach would be to query the database from Python put the information in a seperate database to make it easy to fetch with PHP. Another issue I ran into was browser caching. When a user refreshes my website, ideally a new image should show up every ~5 minutes. But, because of browser caching this was not the case. I tried to set some flags to tell the browser not to cache, but that didn't seem to work. I know there is a flag in the GET request that the browser sends that would tell it not to cache, but I can't control a user's browser. I'm sure there is a good way to fix this issue, but I wasn't able to find it in the limited time that I have.

# In The Future
While this project was mainly just for artistic purposes, I've had a vision of where I want to take this website. Now that the image fetching aspect is set up, I could use all that information for something useful. My idea was to try to associate the colors on an album cover with the mood or genre of a song. So if someone wanted to listen to happy music, my algorithm would be able to select some albums that were categorized as happy using machine learning. I don't think this would be necessarily too hard, I just need to find a way to categorize albums by their mood. That is the hard part.
