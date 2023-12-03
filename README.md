
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Dokumentum</title>
</head>
<body>
    <img id="myImage" src="sad.webp" style="width: 200px;height: 200px;" onmouseenter="csere()" onmouseleave="vcsere()">
    <script>
        function csere() {
            document.getElementById("myImage").src = "hepi.jpg";
        }

        function vcsere() {
            document.getElementById("myImage").src = "sad.webp";
        }
    </script>
<label for="colorList">Válassz egy színt:</label>
<select id="colorList" onchange="changeTextColor()">
    <option value="" selected disabled>Válassz színt...</option>
    <option value="red">Piros</option>
    <option value="green">Zöld</option>
    <option value="blue">Kék</option>
    <option value="yellow">Sárga</option>
    <option value="orange">Narancs</option>
</select>

<p id="colorfulText" style="margin-top: 20px;">
    Ez egy hosszabb szöveg tetszőleges témakörben. Amikor kiválasztasz egy színt a listából,
    a szöveg színe megváltozik a kiválasztott színre.
</p>

<script>
    function changeTextColor() {
        var colorList = document.getElementById("colorList");
        var colorfulText = document.getElementById("colorfulText");
        var selectedColor = colorList.value;

        if (selectedColor) {
            colorfulText.style.color = selectedColor;
        } else {
            colorfulText.style.color = "";
        }
    }
</script>
<label for="number1">Első szám:</label>
    <input type="number" id="number1" name="number1" required>

    <label for="number2">Második szám:</label>
    <input type="number" id="number2" name="number2" required>

    <br>

    <label>Matematikai művelet:</label>
    <input type="radio" id="addition" name="operation" value="addition" checked>
    <label for="addition">Összeadás</label>

    <input type="radio" id="subtraction" name="operation" value="subtraction">
    <label for="subtraction">Kivonás</label>

    <input type="radio" id="multiplication" name="operation" value="multiplication">
    <label for="multiplication">Szorzás</label>

    <input type="radio" id="division" name="operation" value="division">
    <label for="division">Osztás</label>

    <br>

    <button onclick="calculate()">Számol</button>

    <p id="result" style="margin-top: 20px;"></p>

    <script>
        function calculate() {
            var number1 = parseFloat(document.getElementById("number1").value);
            var number2 = parseFloat(document.getElementById("number2").value);
            var operation = getSelectedOperation();
            var resultElement = document.getElementById("result");

            if (!isNaN(number1) && !isNaN(number2)) {
                var result;
                switch (operation) {
                    case "addition":
                        result = number1 + number2;
                        break;
                    case "subtraction":
                        result = number1 - number2;
                        break;
                    case "multiplication":
                        result = number1 * number2;
                        break;
                    case "division":
                        if (number2 !== 0) {
                            result = number1 / number2;
                        } else {
                            result = "Cannot divide by zero";
                        }
                        break;
                    default:
                        result = "Invalid operation";
                }
                resultElement.textContent = "Eredmény: " + result;
            } else {
                resultElement.textContent = "Kérem adjon meg érvényes számokat!";
            }
        }

        function getSelectedOperation() {
            var radios = document.getElementsByName("operation");
            for (var i = 0; i < radios.length; i++) {
                if (radios[i].checked) {
                    return radios[i].value;
                }
            }
            return null;
        }
    </script>
        <h2>Aktuális Dátum és Idő:</h2>
        <p id="currentDateTime"></p>

<script>
            function getCurrentDateTime() {
                var currentDate = new Date();
    
                var day = currentDate.getDate();
                var month = currentDate.getMonth() + 1; 
                var year = currentDate.getFullYear();
    
                var hours = currentDate.getHours();
                var minutes = currentDate.getMinutes();
                var seconds = currentDate.getSeconds();

                var formattedDateTime = day + "/" + month + "/" + year + " " + hours + ":" + minutes + ":" + seconds;
    
                return formattedDateTime;
            }
    
            function updateDateTime() {
                document.getElementById("currentDateTime").textContent = getCurrentDateTime();
            }
    
            setInterval(updateDateTime, 1000);
    
            updateDateTime();
        </script>

        <script>

            var tomb1 = [1, 2, 3];
            var tomb2 = [4, 5, 6];
    

            var szamok = tomb1.concat(tomb2);
            document.write("Eredmény: " + szamok.join(", ") + "</br>");
    

            var legnagyobb = Math.max.apply(null, szamok);
            var legkisebb = Math.min.apply(null, szamok);
    
            // Kiíratás
            document.write("Legnagyobb szám: " + legnagyobb + "</br>");
            document.write("Legkisebb szám: " + legkisebb + "</br>");
    
        for (var i = 0; i < szamok.length; i++) {
            if (szamok[i] % 2 === 0) {
                szamok.splice(i, 1, "páros");
            } else {
                szamok.splice(i, 1, "páratlan");
            }
        }
        document.write("Eredmény: " + szamok.join(", ") + "</br>");
            szamok.push("itt a tömb vége");
            szamok.unshift("itt a tömb eleje");
            document.write("Eredmény: " + szamok.join(", ") + "</br>");
            szamok.reverse();
            document.write("Eredmény: " + szamok.join(", ") + "</br>"+"<br/>");
        </script>  

<script>
    var ellenorzo = "Hamarosan ellenőrző webprogramozásból. Sokat fogok rá tanulni, ígérem.";
    document.write(ellenorzo + "<br>");
    var elsoMondat = ellenorzo.split('. ')[0];
    document.write("Első mondat: " + elsoMondat + "<br>");
    elsoMondat = elsoMondat.toUpperCase();
    document.write("Első mondat csupa nagybetűvel: " + elsoMondat + "<br>");
</script>

<script>
    var szam = 5.50;
    var felfeleKerekitve = Math.ceil(szam);
    document.write("Kerekítve felfelé: " + felfeleKerekitve + "<br>");
    var lefeleKerekitve = Math.floor(szam);
    document.write("Kerekítve lefelé: " + lefeleKerekitve + "<br>");
    var harmadikHatvany = Math.pow(szam, 3);
    document.write("Harmadik hatványra emelve: " + harmadikHatvany + "<br>");
    var negyzetgyok = Math.sqrt(szam);
    document.write("Négyzetgyök: " + negyzetgyok + "<br>");
</script>
</body>
</html>
        
