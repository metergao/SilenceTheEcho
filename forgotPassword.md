
<html>

<head>
  <title>Silence the Echo</title>
</head>

<body>
  <form action="https://silencetheecho.github.io/SilenceTheEcho/passwordReset" method="get">
  <h2>Reset Password</h2>
   <h3>Please enter the email associated with your Silence the Echo account.  </h3>
   <h3>You will receive an email containing a link to reset your password.</h3>
    <div>
      <input id="email" type="text" placeholder="Email...">
    </div>
      <div>
      <button id="submit" type="submit">Reset PasswordSubmit</button>
    </div>
  </form>
  
  
  
    

  <!--Include firebase.js  -->
  
<script src="https://www.gstatic.com/firebasejs/4.6.2/firebase.js"></script>
<script>
 var auth = firebase.auth();
var emailAddress = "user@example.com";

auth.sendPasswordResetEmail(emailAddress).then(function() {
  // Email sent.
}).catch(function(error) {
  // An error happened.
});

</script>
</body>
