---
layout: page
title: Geheimer Bereich
subtitle: Was Frau Schneider so im Geheimen macht
---

<style>
        :root {
            --color: #3d6a78;
            --color-accent: #3d6a781f;
            --color-text: #333;
            --width-content: 768px;
        }

        form {
            background: var(--color-bg);
            width: 22rem;
        }

        #hint {
            cursor: pointer;
        }

        .solution-text,
        .solution-container,
        .hint1-text,
        .hint2-text {
            display: none;
        }
        .hint3-text {
            display: none;
        }

        .solution-container img {
            max-width: 50vw;
        }

        a {
            color: var(--color);
            cursor: pointer;
        }

        @media (max-width: 768px) {
            .solution-container img {
                max-width: 90vw;
            }
        }
</style>

<section>
    <form id="puzzle">
        <header>
            <h2>NUR MIR PASSWORT!</h2>
            <p>Wie lautet das Passwort für den geheimen Bereich?</p>
        </header>

    <!-- Hier beliebig viele Inputs einfügen -->
    <label for="input_01">Lösung:</label>
    <input type="text" id="input_01" name="input_01" size="28" placeholder="Code">

    <button type="submit">Absenden</button><br>

    <a id="hint1"><i>Hinweis 1</i></a><br>
    <div class="hint1-text">
        <div><i>Baut Dinge zusammen, die zusammen gehören</i></div>
        <a id="hint2"><i>Hinweis 2</i></a><br>  
    </div>    

    <div class="hint2-text"> 
        <div><i>Benutzt die "Taschenlampe" und die Batterien</i></div>
        <a id="hint3"><i>Hinweis 3</i></a><br> 
    </div>

    <div class="hint3-text">
        <div><i>Nicht alles ist weiß, was weiß scheint</i></div>
        <a id="solution-link"><i>Lösung anzeigen</i></a><br>  
    </div>  
                
    <div class="solution-text">
        <div><b>HerrSchneider</b></div>
    </div>
</form>
</section>

<section style="margin-top: 1rem;">
    <div class="solution-container">
                
        <div><i>Geht auf folgende Seite: </i></div><br>

        <audio controls>
            <source src="https://raw.githubusercontent.com/FrauSchneider/FrauSchneider.github.io/master/Morse_Code.wav" type="audio/wav">
          </audio>
                
    </div>
</section>

<script  data-cfasync="false">
    window.addEventListener("DOMContentLoaded", event => {
        let hint1Button = document.getElementById("hint1");
        hint1Button.addEventListener("click", (e) => {
            e.preventDefault();
            document.querySelector(".hint1-text").style.display = "inline-block";
        })
        
        let hint2Button = document.getElementById("hint2");
        hint2Button.addEventListener("click", (e) => {
            e.preventDefault();
            document.querySelector(".hint2-text").style.display = "inline-block";
        })

        let hint3Button = document.getElementById("hint3");
        hint3Button.addEventListener("click", (e) => {
            e.preventDefault();
            document.querySelector(".hint3-text").style.display = "inline-block";
        })

        let solutionLink = document.getElementById("solution-link");
        solutionLink.addEventListener("click", (e) => {
            e.preventDefault();
            document.querySelector(".solution-text").style.display = "inline-block";
        })

    });

    function validateForm(answers) {
        let allCorrect = true;
        for (id in answers) {
            let el = document.getElementById(id).value;
            if (el != answers[id]) {
                // incorrect
                alert("Der Code ist nicht korrekt.")
                allCorrect = false;
                break;
            }
        }
        if (allCorrect) {
            // win condition
            revealSolution();
        }
    }

    function revealSolution() {
        document.querySelector(".solution-container").style.display = "block";
    }

    document.getElementById("puzzle").addEventListener("submit", function (e) {
        e.preventDefault();
        // Hier die Lösungsworte und ids eintragen
        validateForm({
            "input_01": "HerrSchneider"
        });
    })
</script>
        