from pathlib import Path

# HTML content of the fake virus prank page
html_content = """
<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <title>Suppression de fichier - snapCompte_v4.db</title>
    <style>
        body {
            background-color: #111;
            color: #eee;
            font-family: 'Courier New', Courier, monospace;
            text-align: center;
            padding-top: 80px;
        }
        .danger {
            color: #ff4444;
            font-size: 22px;
        }
        .file {
            color: #00ffcc;
            font-weight: bold;
        }
        button {
            font-size: 18px;
            margin: 20px;
            padding: 12px 24px;
            cursor: pointer;
            background-color: #333;
            color: #fff;
            border: 2px solid #666;
        }
        .hidden {
            display: none;
        }
        #loader {
            margin-top: 30px;
            font-size: 20px;
        }
    </style>
</head>
<body>

    <h1>🗂️ Fichier détecté : <span class="file">snapCompte_v4.db</span></h1>
    <p class="danger">Ce fichier semble obsolète. Souhaitez-vous le supprimer ?</p>

    <div id="buttons">
        <button onclick="beginFakeDeletion()">✅ Oui, supprime-le</button>
        <button onclick="beginFakeDeletion()">❌ Non, je le garde</button>
    </div>

    <div id="autoDelete" class="hidden danger">
        ⏱️ Aucune réponse détectée.<br>Suppression automatique de <span class="file">snapCompte_v4.db</span> en cours...
    </div>

    <div id="loader" class="hidden">Suppression en cours...</div>
    <div id="result" class="hidden">
        <h2>💀 Suppression terminée.</h2>
        <p>... enfin non. T’as juste perdu 1 minute de ta vie pour rien 🤣🫵🏽🤣🫵🏽</p>
    </div>

    <script>
        let triggered = false;

        function beginFakeDeletion() {
            if (triggered) return;
            triggered = true;

            document.getElementById("buttons").classList.add("hidden");
            document.getElementById("loader").classList.remove("hidden");

            setTimeout(() => {
                document.getElementById("loader").classList.add("hidden");
                document.getElementById("result").classList.remove("hidden");
            }, 60000); // 1 minute
        }

        setTimeout(() => {
            if (!triggered) {
                document.getElementById("buttons").classList.add("hidden");
                document.getElementById("autoDelete").classList.remove("hidden");
                beginFakeDeletion();
            }
        }, 10000); // 10 secondes sans réponse
    </script>

</body>
</html>
"""

# Save the file
file_path = Path("/mnt/data/fake_virus_snap.html")
file_path.write_text(html_content)

file_path

