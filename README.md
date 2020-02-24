# complete-easy
An easy but complete project, using React, Firebase

In this project I was planing on using the following techniques.
* GitHub
* React
* Firebase Hosting
* Firebase Database
* GraphQL
* Travis (CI)
* and maybe something more

# React #
We start by creating a react app. We will be using Create React App to bootstrap our application. But first some other steps.
1. We need npm for this project. (You could also use yarn, but I will not cover that right now). 
2. Npm comes with node.js, so could check if you have node by typing `node -v` and then `npm -v` in a terminal. If you havn't got any of them. You could download node from here https://nodejs.org/en/ .
Even if you have npm, it could be good to download the latest version by typing ´npm install npm@latest -g´.
3. Go to a folder of your choice.  I've choosen ~/projects  (on mac), which is equal as C:\Users\arisaLinnea\projects on a windows machine.
4. Type `npx create-react-app my-app`   where my-app could be changed to whatever you want.
5. (Here you could use `npm init react-app my-app` or `yarn create react-app my-app` instead. If you used create-react-app before, but not recently, it might be a good idea to use `npm uninstall -g create-react-app``
6. Now you should have a new folder with the name you chose.

# GitHub #
New lets create a repository on GitHub. 

1. Log in with your account on GitHub. 
2. Choose to create a new repository. 
3. Choose the same name as your react project.
4. Deside if it should be public or private. 
5. Open a terminal on your computer and navigate to the folder with your react project.
7. If it's the first time you access a repo on your github on that computer, you will need to install git and create ssh key. (We will be using the key to later on to push and pull changes.) A new key needs to be saved for every computer you use.
   - Check if you have git by writing `git --version`
   - If you don't have git, please follow the steps here: https://git-scm.com/book/en/v2/Getting-Started-Installing-Git
   - Check credentials `git config --list`
   - If there is not credentials (if you just installed git) or want to change credentials
     - `git config --global user.name "Your name here"`
     - `git config --global user.email "your_email@example.com"`
     - You can skip to --global if you want different local credentials for different folders
   - Check if you have ~/.ssh/id_rsa and ~/.ssh/id_rsa.pub
     - If not generete with `ssh-keygen -t rsa -C "your_email@example.com"`
     - You can press enter on filename to get the default name
     - You can press enter on passphrase if you don't want any.
   - Open the id_rsa.pub  ( `less id_rsa.pub` ) and copy the content.
   - Go to your github account on the browser.
   - Under Settings -> SSH and GPG keys, press "new SSH key"   
   - Choose a name and paste the copied content. Save.
8. Write `git init`
7. `git add .`  to add all files
8. `git commit -m "First commit"`
9. Go to the repository that you earlier created. And press "Clone or download". Copy the link for ssh.
10. Go to the terminal and write `git remote add origin [ssh link that you copied]`   
11. To be sure, write `git remove -v` to see that it's linked to the right repo.
12. `git push -u origin master`

## Available Scripts

In the project directory, you can run:

### `npm start`

Runs the app in the development mode.<br />
Open [http://localhost:3000](http://localhost:3000) to view it in the browser.

The page will reload if you make edits.<br />
You will also see any lint errors in the console.

### `npm test`

Launches the test runner in the interactive watch mode.<br />
See the section about [running tests](https://facebook.github.io/create-react-app/docs/running-tests) for more information.

### `npm run build`

Builds the app for production to the `build` folder.<br />
It correctly bundles React in production mode and optimizes the build for the best performance.

The build is minified and the filenames include the hashes.<br />
Your app is ready to be deployed!

See the section about [deployment](https://facebook.github.io/create-react-app/docs/deployment) for more information.

### `npm run eject`

**Note: this is a one-way operation. Once you `eject`, you can’t go back!**

If you aren’t satisfied with the build tool and configuration choices, you can `eject` at any time. This command will remove the single build dependency from your project.

Instead, it will copy all the configuration files and the transitive dependencies (webpack, Babel, ESLint, etc) right into your project so you have full control over them. All of the commands except `eject` will still work, but they will point to the copied scripts so you can tweak them. At this point you’re on your own.

You don’t have to ever use `eject`. The curated feature set is suitable for small and middle deployments, and you shouldn’t feel obligated to use this feature. However we understand that this tool wouldn’t be useful if you couldn’t customize it when you are ready for it.

## Learn More

You can learn more in the [Create React App documentation](https://facebook.github.io/create-react-app/docs/getting-started).

To learn React, check out the [React documentation](https://reactjs.org/).

### Code Splitting

This section has moved here: https://facebook.github.io/create-react-app/docs/code-splitting

### Analyzing the Bundle Size

This section has moved here: https://facebook.github.io/create-react-app/docs/analyzing-the-bundle-size

### Making a Progressive Web App

This section has moved here: https://facebook.github.io/create-react-app/docs/making-a-progressive-web-app

### Advanced Configuration

This section has moved here: https://facebook.github.io/create-react-app/docs/advanced-configuration

### Deployment

This section has moved here: https://facebook.github.io/create-react-app/docs/deployment

### `npm run build` fails to minify

This section has moved here: https://facebook.github.io/create-react-app/docs/troubleshooting#npm-run-build-fails-to-minify
