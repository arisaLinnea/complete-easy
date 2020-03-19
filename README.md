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
7. Write `npm start` in the terminal and you will than be able to see the new react app in the browser: http://localhost:3000/

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
11. To be sure, write `git remote -v` to see that it's linked to the right repo.
12. `git push -u origin master`
13. Go to GitHub in the browser and check that your new files are in the repo.


# Firebase Hosting and Firebase Storage#
For this project I want to use Firebase to host my project and also use some storage for data. Firebase have several ways to store data. I will choose **Storage**. You can read more here firebase.google.com/docs/database/rtdb-vs-firestore if you are unsure which will work best for you.
1. Go to Firebase webpage (firebase.google.com) , login/create account. Go to the console on the firebase webpage.
2. Add Project
3. Set a name
4. Enable Google Analytics, if you want to.
5. When project is created, go to **Storage** in the left menu.
   - Info about importance of defining rules. However nothing we will do in this step.
   - Choose a location. This can't be changed later on, so choose visely. 
   - Press **Done** and wait.
6. Go to **Hosting** on the left meny. And press 'get started'.
7. As it says on the set up, we need to install Firebase CLI. (I didn't check the checkbox for Firebase JS SDK).
   - Go to the terminal and your project folder.
   - Enter `npm install -g firebase-tools`  (The -g will install it globally, so you have it for other projects. But can always run the command again then, to insure that you have the latest version).
8. Lets go to the next step of setting up Firebase hosting on the webpage.
9. From terminal, enter `firebase login` in the root of your project.
   - Answer question according to own preferences.
   - Login in using your google account credentials and let Firebase access your account.
   - Close window / tab
   - In terminal you should see a success message.
10. From terminal, enter `firebase init`   (from project root)
    - We want **hosting**, so select that one.
    - I will also choose **Storage**. 
    - Confirm by pressing enter.
    - We will choose 'Existing project'
    - Choose the name of the project we recently created on firebase website.
    - I will choose **build** as my public directory
    - **Yes** For single-page app
    - **N** for overwrite index.html
    - I choose **storage.rules** for the storage rules
    - Done
11. `firebase deploy`
12. If you go to [name of your firebase project].web.app you will probably not see anything. That's because we har missing some things in our index.html (that we didn't want to overwrite).
    - Go to Project Overview on firebase website.
    - At the bottom of **General**, Use to add a app. (of type web). 
    - Choose a nickname
    - Register app.
    - Copy code segment
    - Under **general**, you should now be able to see the app. Under **Linked Firebae Hosting site**, choose the one we created above.
    - Open your index.html file.
    - Add the copied content just above `<div id="root"></div>` in the body tag.
    - `npm run build` in the terminal
    - `firebase deploy` in the terminal
13. Can now see it on [name of your firebase project].web.app

# Travis CI #
We have now deployed to Firebase and can see the react site on the url what Firebase Hosting has given us. For every change we do we need to run the `firebase deploy` command and the new stuff will be shown. However, we use GitHub and might have several contributers that change to code. We want the version that's the latest in GitHub to be the one that is shown on our hosting url. But How do we invoke a firebase deploy from GitHub?
I was planing on using Travis. Travis is a Continuous Integration service. Since this is open source code, I can use travis for free.
1. Go to the root of your project and create a file called **.travis.yml**
2. Look at the .travis.yml file here on the github repo, but basically it will have the following:
   - `language: node_js`
   - `node_js:`   version
3. To set the $FIREBASE_TOKEN
   - Go to the terminal
   - `firebase login:ci`
   - Login in and give access to firebase
   - Close browser window / tab
   - In terminal, copy the token that is shown.
   - Go to the Travis webpage (travis-ci.org). 
   - I signed in with by google account.
   - On your account page you should be able to see all your github repos. 
     - Press the one you have been working on for this project.
     - Choose to active it.
   - On your repo page, choose settings (Might be hiden under the hamburger menu.
   - Under environment varibles
   - Add a new Variable named **FIREBASE_TOKEN** and with the value of the copied token.
4. Now everything is finished in travis, lets test it.
5. Open your project in a editor, and make a change in App.js. (For example change the text inside the <p> to 'Hello Firebase and Travis'.)
6. Go to the terminal and write `git add .`, `git commit -m "changed text"` and `git push`.
7. Now you should see logs in travis.
8. Check the firebase url and see if it's been updated with the new text.
   
# More Firebase Storage #


### Making a Progressive Web App

This section has moved here: https://facebook.github.io/create-react-app/docs/making-a-progressive-web-app


