        //this java code calls the Google Sheet url that the user info is sent to upon submitting button.
        const scriptURL = 'https://script.google.com/macros/s/AKfycbytVfUKG020TJjqYtHvge9h7k8FortVu02sixb0I_Z03EPs0FJSjJ2ogdyt	-X64oDUI6g/exec'
        const form = document.forms['submit-to-google-sheet']
        //this calls the span name that will display a thank you message once the user signs up and clears 	the input fields
        const thankYou = document.getElementById("thankYou");
      
        form.addEventListener('submit', e => {
          e.preventDefault()
          fetch(scriptURL, { method: 'POST', body: new FormData(form)})
          //this response calls the span again from HTML and replaces it with the message
          //setTimeout is set to 5s where the form is resetted(form.reset)
            .then(response => {
                thankYou.innerHTML = "You are signed up. We will be in touch!"
                setTimeout(function(){thankYou.innerHTML = ""},5000)})
                form.reset()
            .catch(error => console.error('Error!', error.message))
        })