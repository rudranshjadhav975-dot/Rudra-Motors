# Rudra-Motors
car bussiness app
[rudra motors app.zip]([index.html](https://github.com/user-attachments/files/22762669/index.html)
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Car Buyer App</title>
    <link rel="stylesheet" href="styles.css">
</head><!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Car Buyer App</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <header>
        <h1>Rudra Motors</h1>
    </header>

    <main>
        <input type="text" id="searchBox" placeholder="Search cars..." onkeyup="filterCars()">

        <div id="carList" class="car-list"></div>
    </main>

    <script src="script.js"></script>
</body>
</html>

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Seller Portal</title>
    <style>
        body { font-family: Arial; background: #121212; color: white; padding: 20px; }
        h1 { text-align: center; }
        input, button { display: block; margin: 10px 0; padding: 10px; width: 100%; }
        input { border-radius: 5px; border: none; }
        button { border: none; background: #ff5722; color: white; border-radius: 5px; cursor: pointer; }
        button:hover { background: #e64a19; }
        #formContainer { display: none; }
    </style>
</head>
<body>
    <h1>Seller Portal</h1>

    <div id="loginContainer">
        <input type="password" id="passwordInput" placeholder="Enter Seller Password">
        <button onclick="checkPassword()">Login</button>
    </div>

    <div id="formContainer">
        <h2>Add Car</h2>
        <input id="carName" placeholder="Car Name">
        <input id="carPrice" placeholder="Car Price">
        <input id="carImage" placeholder="Car Image URL">
        <input id="carContact" placeholder="Seller Contact">
        <button onclick="addCar()">Add Car</button>

        <h2>Your Cars</h2>
        <div id="carList"></div>
    </div>

    <script>
        const SELLER_PASSWORD = "Rudra@2013"; // Change this to your own password

        function checkPassword() {
            const pass = document.getElementById("passwordInput").value;
            if (pass === SELLER_PASSWORD) {
                document.getElementById("loginContainer").style.display = "none";
                document.getElementById("formContainer").style.display = "block";
                loadCars();
            } else {
                alert("Incorrect password!");
            }
        }

        function loadCars() {
            let cars = JSON.parse(localStorage.getItem("cars") || "[]");
            displayCars(cars);
        }

        function addCar() {
            const name = document.getElementById("carName").value;
            const price = document.getElementById("carPrice").value;
            const image = document.getElementById("carImage").value;
            const contact = document.getElementById("carContact").value;

            if (!name || !price || !image || !contact) {
                alert("Please fill all fields!");
                return;
            }

            let cars = JSON.parse(localStorage.getItem("cars") || "[]");
            cars.push({ name, price, image, contact });
            localStorage.setItem("cars", JSON.stringify(cars));

            document.getElementById("carName").value = "";
            document.getElementById("carPrice").value = "";
            document.getElementById("carImage").value = "";
            document.getElementById("carContact").value = "";

            loadCars();
            alert("Car added successfully!");
        }

        function displayCars(cars) {
            const carList = document.getElementById("carList");
            carList.innerHTML = "";

            cars.forEach((car, index) => {
                let div = document.createElement("div");
                div.style.background = "#1f1f1f";
                div.style.margin = "10px";
                div.style.padding = "10px";
                div.style.borderRadius = "8px";

                div.innerHTML = `
                    <h3>${car.name}</h3>
                    <p><strong>Price:</strong> ${car.price}</p>
                    <img src="${car.image}" alt="${car.name}" style="width:100%;border-radius:5px;">
                    <p><strong>Contact:</strong> ${car.contact}</p>
                    <button onclick="deleteCar(${index})">Delete Car</button>
                `;
                carList.appendChild(div);
            });
        }

        function deleteCar(index) {
            let cars = JSON.parse(localStorage.getItem("cars") || "[]");
            cars.splice(index, 1);
            localStorage.setItem("cars", JSON.stringify(cars));
            loadCars();
        }
    </script>
</body>
</html>


<p><strong>Contact:</strong></p>
<a href="tel:9890050121"><button style="padding:8px 12px; margin:5px; background:#ff5722; color:white; border:none; border-radius:5px;">Call 9890050121</button></a>
<a href="tel:8830109185"><button style="padding:8px 12px; margin:5px; background:#ff5722; color:white; border:none; border-radius:5px;">Call 8830109185</button></a>
