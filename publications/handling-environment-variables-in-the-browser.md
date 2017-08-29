# Handling environment variables in the browser

Front end projects usually make use of external resources through URLs, API Keys, etc. Those things may change depending on which environment you are running your code. If you are in a development environment, you don’t want to mess your metrics like Mixpanel or Google Analytics, for example.

Although it is a very basic need, it is not hard to find projects doing a variety of tricks to handle this. The solutions are often not clear. Sometimes, more code is written to decide which value to use, making things difficult when you need to make changes on it.

One of my last projects was built using Aurelia framework through Aurelia CLI. Since then, I have learned a simple and clear way of dealing with environment variables. Following the Aurelia CLI approach, I currently get a crystal clear environment variables management with just a couple files and one gulp task. Check them out:

[GIST](https://gist.github.com/rafaelcamargo/f916d0d9e76d66848a16c236453594c2)

Now, when running gulp with `--env=prod` flag, the variables for production environment will be used. Otherwise, the default (dev) environment variables will be used.

If you have controlled environment variables for your project in a different and more interesting way, please, don’t hesitate to share it in the comments.
