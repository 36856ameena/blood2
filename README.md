<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Online Blood Donation System</title>
  <link rel="stylesheet" href="style.css" />
</head>
<body>
  <nav>
    <h1>BloodConnect</h1>
    <ul>
      <li><a href="index.html">Home</a></li>
      <li><a href="register.html">Register</a></li>
      <li><a href="view.html">View Donors</a></li>
    </ul>
  </nav>

  <section class="hero">
    <div class="hero-text">
      <h2>Donate Blood, Save Lives</h2>
      <p>Your small act of kindness can give someone another chance to live.</p>
      <div class="buttons">
        <a href="register.html" class="btn">Register Now</a>
        <a href="view.html" class="btn-outline">Find Donor</a>
      </div>
    </div>
  </section>

  <footer>
    <p>© 2025 BloodConnect | Made with ❤️</p>
  </footer>
</body>
</html>
!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Register - BloodConnect</title>
  <link rel="stylesheet" href="style.css" />
</head>
<body>
  <nav>
    <h1>BloodConnect</h1>
    <ul>
      <li><a href="index.html">Home</a></li>
      <li><a href="register.html" class="active">Register</a></li>
      <li><a href="view.html">View Donors</a></li>
    </ul>
  </nav>

  <section class="form-section">
    <h2>Register as Donor or Receiver</h2>
    <form id="registerForm">
      <input type="text" id="name" placeholder="Full Name" required />
      <input type="number" id="age" placeholder="Age" required />
      <input type="text" id="bloodGroup" placeholder="Blood Group (A+, O-, etc)" required />
      <input type="text" id="city" placeholder="City" required />
      <input type="text" id="contact" placeholder="Contact Number" required />
      <select id="role" required>
        <option value="">Select Role</option>
        <option value="Donor">Donor</option>
        <option value="Receiver">Receiver</option>
      </select>
      <button type="submit" class="btn">Submit</button>
    </form>
  </section>

  <footer>
    <p>© 2025 BloodConnect</p>
  </footer>

  <script src="script.js"></script>
</body>
</html>
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>View Donors - BloodConnect</title>
  <link rel="stylesheet" href="style.css" />
</head>
<body>
  <nav>
    <h1>BloodConnect</h1>
    <ul>
      <li><a href="index.html">Home</a></li>
      <li><a href="register.html">Register</a></li>
      <li><a href="view.html" class="active">View Donors</a></li>
    </ul>
  </nav>

  <section class="view-section">
    <h2>Available Donors & Receivers</h2>
    <input type="text" id="searchCity" placeholder="Search by City..." />
    <div id="dataContainer" class="card-container"></div>
  </section>

  <footer>
    <p>© 2025 BloodConnect</p>
  </footer>

  <script src="script.js"></script>
</body>
</html>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: "Poppins", sans-serif;
}

body {
  background-color: #fafafa;
  color: #333;
}

nav {
  background-color: #6b0f1a;
  color: white;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 1rem 2rem;
}

nav h1 {
  font-size: 1.5rem;
  letter-spacing: 1px;
}

nav ul {
  list-style: none;
  display: flex;
  gap: 1.2rem;
}

nav a {
  color: white;
  text-decoration: none;
  transition: 0.3s;
}

nav a:hover, .active {
  color: #ffd6d6;
}

.hero {
  background: linear-gradient(rgba(0,0,0,0.4), rgba(0,0,0,0.4)), url('https://i.imgur.com/lxZxJ5M.jpg') center/cover no-repeat;
  height: 80vh;
  display: flex;
  align-items: center;
  justify-content: center;
  color: white;
  text-align: center;
}

.hero h2 {
  font-size: 2.5rem;
  margin-bottom: 1rem;
}

.btn, .btn-outline {
  padding: 0.7rem 1.5rem;
  border-radius: 8px;
  border: none;
  cursor: pointer;
  margin: 0.5rem;
  font-weight: 600;
}

.btn {
  background-color: #8b0000;
  color: white;
}

.btn-outline {
  background-color: transparent;
  border: 2px solid white;
  color: white;
}

.form-section, .view-section {
  padding: 2rem;
  text-align: center;
}

form {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 1rem;
  margin-top: 1rem;
}

form input, select {
  width: 300px;
  padding: 0.7rem;
  border: 1px solid #ccc;
  border-radius: 6px;
}

.card-container {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 1rem;
  margin-top: 2rem;
}

.card {
  background-color: white;
  border-radius: 10px;
  padding: 1rem;
  box-shadow: 0 2px 6px rgba(0,0,0,0.1);
  width: 250px;
}

.card h3 {
  color: #8b0000;
}

footer {
  text-align: center;
  padding: 1rem;
  background-color: #6b0f1a;
  color: white;
  margin-top: 3rem;
}
// Save registration data to LocalStorage
document.addEventListener("DOMContentLoaded", () => {
  const form = document.getElementById("registerForm");
  const dataContainer = document.getElementById("dataContainer");
  const searchCity = document.getElementById("searchCity");

  if (form) {
    form.addEventListener("submit", (e) => {
      e.preventDefault();
      const person = {
        name: form.name.value,
        age: form.age.value,
        bloodGroup: form.bloodGroup.value,
        city: form.city.value,
        contact: form.contact.value,
        role: form.role.value,
      };

      let data = JSON.parse(localStorage.getItem("bloodData")) || [];
      data.push(person);
      localStorage.setItem("bloodData", JSON.stringify(data));

      alert("Registration successful!");
      form.reset();
    });
  }

  if (dataContainer) {
    function displayData(filter = "") {
      let data = JSON.parse(localStorage.getItem("bloodData")) || [];
      dataContainer.innerHTML = "";
      data
        .filter((item) =>
          item.city.toLowerCase().includes(filter.toLowerCase())
        )
        .forEach((person) => {
          const card = document.createElement("div");
          card.classList.add("card");
          card.innerHTML = `
            <h3>${person.name}</h3>
            <p><b>Role:</b> ${person.role}</p>
            <p><b>Blood Group:</b> ${person.bloodGroup}</p>
            <p><b>City:</b> ${person.city}</p>
            <p><b>Age:</b> ${person.age}</p>
            <p><b>Contact:</b> ${person.contact}</p>
          `;
          dataContainer.appendChild(card);
        });
    }

    displayData();

    if (searchCity) {
      searchCity.addEventListener("input", (e) => {
        displayData(e.target.value);
      });
    }
  }
});
