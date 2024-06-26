![ekran](https://github.com/volkanbasaran1/firebase_auth/assets/76842256/100e99ea-0bb8-48a1-a7e0-9165f6e60e71)
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Firebase Auth Kullanımı</title>
</head>
<body>
    <h1>Firebase Auth Kullanımı</h1>
    <h2>Adımlar:</h2>
    <ol>
        <li>Firebase Console'a gidin ve yeni bir proje oluşturun.</li>
        <li>Oluşturduğunuz projeye Firebase Authentication özelliğini ekleyin.</li>
        <li>Projeyi ayarlarınıza giderek, web uygulamanızı Firebase'e ekleyin. Bu işlem sonucunda bir Firebase yapılandırma objesi alacaksınız.</li>
        <li>İlgili Firebase SDK'sını HTML sayfanıza ekleyin:
            ```html
            <!-- Firebase JavaScript SDK -->
            <script src="https://www.gstatic.com/firebasejs/9.1.0/firebase-app.js"></script>
            <script src="https://www.gstatic.com/firebasejs/9.1.0/firebase-auth.js"></script>
            <script src="https://www.gstatic.com/firebasejs/9.1.0/firebase-firestore.js"></script> <!-- Örneğin Firestore kullanıyorsanız -->
            ```
        </li>
        <li>Firebase yapılandırma objesini ekleyin:
            ```html
            <script>
                var firebaseConfig = {
                    apiKey: "YOUR_API_KEY",
                    authDomain: "YOUR_AUTH_DOMAIN",
                    projectId: "YOUR_PROJECT_ID",
                    storageBucket: "YOUR_STORAGE_BUCKET",
                    messagingSenderId: "YOUR_MESSAGING_SENDER_ID",
                    appId: "YOUR_APP_ID"
                };
                // Firebase'i başlatın
                firebase.initializeApp(firebaseConfig);
            </script>
            ```
        </li>
        <li>Kullanıcıları yönetmek için Firebase Authentication API'sını kullanın:
            ```html
            <script>
                // Yeni bir hesap oluşturmak için
                function signUp() {
                    var email = document.getElementById("email").value;
                    var password = document.getElementById("password").value;
                    firebase.auth().createUserWithEmailAndPassword(email, password)
                        .then((userCredential) => {
                            // Yeni hesap oluşturulduğunda yapılacak işlemler
                            var user = userCredential.user;
                            console.log("Yeni kullanıcı oluşturuldu:", user);
                        })
                        .catch((error) => {
                            // Hata durumunda yapılacak işlemler
                            var errorCode = error.code;
                            var errorMessage = error.message;
                            console.error("Hata:", errorMessage);
                        });
                }
                // Oturum açmak için
                function signIn() {
                    var email = document.getElementById("email").value;
                    var password = document.getElementById("password").value;
                    firebase.auth().signInWithEmailAndPassword(email, password)
                        .then((userCredential) => {
                            // Oturum açıldığında yapılacak işlemler
                            var user = userCredential.user;
                            console.log("Oturum açıldı:", user);
                        })
                        .catch((error) => {
                            // Hata durumunda yapılacak işlemler
                            var errorCode = error.code;
                            var errorMessage = error.message;
                            console.error("Hata:", errorMessage);
                        });
                }
            </script>
            ```
        </li>
    </ol>
    <h2>HTML Form Örneği:</h2>
    <form>
        <label for="email">Email:</label><br>
        <input type="email" id="email" name="email"><br>
        <label for="password">Password:</label><br>
        <input type="password" id="password" name="password"><br><br>
        <button type="button" onclick="signUp()">Kaydol</button>
        <button type="button" onclick="signIn()">Giriş Yap</button>
    </form>
</body>
</html>
