<!--This code was lifted from a firebase how-to-guide https://howtofirebase.com/firebase-authentication-for-web-d58aad62cf6d-->


<html>

<head>
  <title>Silence the Echo Chamber</title>
</head>

<body>
  <form>
  <h1>Silence the Echo Chamber</h1>
  <h2>User Login</h2>
    <div>
      <input id="email" type="text" placeholder="Email...">
    </div>
    <div>
      <input id="password" type="password" placeholder="Password...">
    </div>
    <div>
      <button id="sign-in">Sign In/Register</button>
      <button id="sign-out">Sign Out</button>
    </div>
     <a href="https://silencetheecho.github.io/SilenceTheEcho/forgotPassword">Forgot password?</a> 
  </form>

  <!--Include firebase.js  -->
  
<script src="https://www.gstatic.com/firebasejs/4.6.2/firebase.js"></script>
<script>
  // Initialize Firebase
  var config = {
    apiKey: "AIzaSyAbBnEsH-88WhhZqjG0xczXXriqvYRA_y4",
    authDomain: "silencetheecho-efa5e.firebaseapp.com",
    databaseURL: "https://silencetheecho-efa5e.firebaseio.com",
    projectId: "silencetheecho-efa5e",
    storageBucket: "silencetheecho-efa5e.appspot.com",
    messagingSenderId: "765642044089"
  };
  firebase.initializeApp(config);
</script>
  
  <!--Handle auth events-->
  <script>
    firebase.auth().onAuthStateChanged(function(user) {
      window.user = user;
      // Step 1:
      //  If no user, sign in anonymously with firebase.auth().signInAnonymously()
      //  If there is a user, log out out user details for debugging purposes.
    });
  </script>

  <!--Handle page events-->
  <script>
    document.querySelector('#sign-in').addEventListener('click', function(e) {
      e.preventDefault();
      e.stopPropagation();
      var email = document.querySelector('#email').value;
      var password = document.querySelector('#password').value
      var credential = firebase.auth.EmailAuthProvider.credential(email, password);
      var auth = firebase.auth();
      var currentUser = auth.currentUser;
   //   firebase.auth().signIn(); //added this (DEM)
      firebase.auth.emailAuthProvider.credential(emailInput.value, passwordInput.value);//added this (DEM)
      firebase.auth.signInWithCredential(credential);//added this (DEM)
      // Step 2
      //  Get a credential with firebase.auth.emailAuthProvider.credential(emailInput.value, passwordInput.value)
      //  If there is no current user, log in with auth.signInWithCredential(credential)
      //  If there is a current user an it's anonymous, atttempt to link the new user with firebase.auth().currentUser.link(credential)
      //  The user link will fail if the user has already been created, so catch the error and sign in.
    });
    document.querySelector('#sign-out').addEventListener('click', function(e) {
      e.preventDefault();
      e.stopPropagation();
      firebase.auth().signOut();
    });
  </script>
<div>
     <a href="https://silencetheecho.github.io/SilenceTheEcho">Home</a>  
</div>
<div>
     <a href="https://silencetheecho.github.io/SilenceTheEcho/faqs">FAQS</a>  
</div>
<div>
     <a href="https://silencetheecho.github.io/SilenceTheEcho/search">See it in action</a>  
</div>
<div>
     <a href="https://silencetheecho.github.io/SilenceTheEcho/security">Security and Privacy Standards</a>  
</div>



</body>

