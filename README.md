import { initializeApp } from "firebase/app";
import { getAuth, signInWithEmailAndPassword } from "firebase/auth";

// إعداد Firebase
const firebaseConfig = {
  apiKey: "AIzaSyAaOSLLJZGWicH-Vtnjup0DG-Opbyx4_OE",
  authDomain: "task-manager-site-f0346.firebaseapp.com",
  projectId: "task-manager-site-f0346",
  storageBucket: "task-manager-site-f0346.firebasestorage.app",
  messagingSenderId: "110606706563",
  appId: "1:110606706563:web:45f827ee08f0873decb8b6"
};

// تهيئة Firebase
const app = initializeApp(firebaseConfig);
const auth = getAuth(app);

// دالة تسجيل الدخول
document.getElementById("loginForm").addEventListener("submit", function(event) {
  event.preventDefault();

  const email = document.getElementById("email").value;
  const password = document.getElementById("password").value;

  signInWithEmailAndPassword(auth, email, password)
    .then((userCredential) => {
      const user = userCredential.user;
      console.log("تم تسجيل الدخول:", user.email);
      // هنا ننتقل للخطوة التالية بعد تسجيل الدخول
      // يمكننا التحقق من دور المستخدم هنا
    })
    .catch((error) => {
      const errorMessage = error.message;
      alert("حدث خطأ: " + errorMessage);
    });
});
