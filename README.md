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

	     
Now you want to config eslint with airbnb.
1. install eslint in your project.
	npm i eslint --save-dev
2. now initialize your environment with the following command.
	./node_modules/.bin/eslint --init
	#give all the answers according to your environment
3. Our default export contains all of our ESLint rules, including ECMAScript 6+. It requires eslint and eslint-plugin-import.

Install the correct versions of each package, which are listed by the command:
	 npm info "eslint-config-airbnb-base@latest" peerDependencies

     #now install all the dependencies using this command

     npx install-peerdeps --dev eslint-config-airbnb-base

4.now make a file .eslintrc.js and add following lines
	
	{
	"env": {
		"browser": true,
		"commonjs": true,
		"es2021": true
	},
	"extends": ["airbnb-base"],
	"parserOptions": {
		"ecmaVersion": 12
	},
	"rules": {
		"no-console": "warn"
		#add rules according to your choice. 
	},
	"ignorePatterns": ["node_modules", "*.html", "/assets/**"]
	}

4.now go and instll ESLint extensions in your VSCode.
    
