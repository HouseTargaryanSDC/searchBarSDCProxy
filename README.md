# searchBarSDCProxy

This project was to optimize the top search bar component of a mock Opentable web page to handle high volume traffic as well as optimizing database key word search times. The project was deployed using Docker onto AWS EC2 instances. 

I seeded the database by adding 10M random nouns for cities, cuisines and restaurants. I used loader.io to send requests every second to my server to see how it handles traffic and the response time required. Before any optimization was done, the baseline bottlenecked at 150 RPS with a response time of 88 ms. 

To optimize the search bar, I used nginx as a load balancer, using roundtable method to direct requests to different servers. I also set up four more servers to horizontally scale the application. I also explored PostGreSQL's gin indexing method to index my database. This reduced the text-search query time overall. With optimizations done on the server and database side, the result was the search bar able to handle up to 800 RPS with an average response time of 90 ms. 

Note: This project is currently not seeded with 10M entries and the remote AWS database is currently stopped. Screenshots are provided for visualizing the optimization results. 


Before optimization: 
![alt text](https://s3-us-west-1.amazonaws.com/fecdemo/dan%2C+400rps.png)

After optimization: 
![alt text](https://s3-us-west-1.amazonaws.com/fecdemo/800+rps%2C+alex.png)

