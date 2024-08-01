how to setup webpack.

1. open project repo.
2. open terminal and initialize your project repo with this command.
      npm init -y
3. make a file setup in your project repo.
      |- /dist
      |- /src
         |- index.js
         |- style.css
         |- index.html #if u want to add custom html template in your project.
      |- gitignore #to ignore node_modules
      |- package.json
      |- package-lock.json
      |- webpack.config.js
      
4. now instll webpack
      npm -i -D webpack webpack-cli webpack-dev-server
      
      #if u have custom html file to load this
      npm -i -D html-webpack-plugin
      
      #also install css loaders
      npm -i -D style-loader css-loader

5. now setup webpack config file
      const HtmlWebpackPlugin = require("html-webpack-plugin");
      const path = require("path");
     
     
      module.exports = {
	  mode: "production" or "development",
	  entry: "./src/index.js",
	  output: {
	    filename: "main.js",
	    path: path.resolve(__dirname, "dist"),
	    clean: true,
	  },
	  
	  
	  devServer: {
	    static: "./dist",
	    open: true,
	    port: 5000,
	  },
	  
	  plugins: [
	    new HtmlWebpackPlugin({
	      template: "./src/index.html",
	    }),
	  ],
	  module: {
	    rules: [
	      {
		test: /\.css$/i,
		use: ["style-loader", "css-loader"],
	      },
	    ],
	  },
       };

	     
