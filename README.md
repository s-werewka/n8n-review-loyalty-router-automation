# n8n-review-loyalty-router-automation
🚀 Automated Customer Feedback & Incident Management System
Automatyczny system do zbierania, analizowania i zarządzania opiniami klientów oparty na n8n, OpenAI, Twilio, Google Sheets oraz Telegramie.
System automatycznie wysyła spersonalizowane formularze po wizycie klienta, analizuje poziom zadowolenia, kategoryzuje negatywny feedback za pomocą sztucznej inteligencji i natychmiastowo alarmuje zespół na Telegramie.
🌟 Kluczowe Funkcje
•	Personalizowane wiadomości SMS: Automatyczna wysyłka linków do formularza przez Twilio z unikalnymi parametrami URL.
•	Bezpieczny przesył danych (Hidden Fields): Dane klienta są przekazywane bezszwowo w tle między krokami formularza.
•	Inteligentna analiza AI (OpenAI): Automatyczna ocena pilności, kategoryzacja problemu oraz generowanie podsumowania i sugerowanej reakcji dla zespołu.
•	Baza danych w Google Sheets: Rejestracja opinii z interaktywną listą rozwijaną (Dropdown) do zarządzania statusami zgłoszeń (Nowe, W trakcie, Zakończono).
•	Powiadomienia Telegram: Natychmiastowe alerty dla zespołu w przypadku ocen 1–3★ z pełnym podsumowaniem i opcją szybkiego reagowania.
•	Obsługa Błędów (Error Handling): Dedykowany workflow wyłapujący awarie API (Error Trigger) z alertami na Telegramie.
🔄 Elastyczność i Triggery
System został zaprojektowany w sposób modułowy. Choć domyślnie proces inicjowany jest przez zdarzenia w skrzynce pocztowej (Gmail), dzięki architektury n8n wyzwalacz (Trigger) można łatwo podmienić na:
•	Google Sheets Trigger: Uruchomienie automatyzacji po dodaniu nowego wiersza w arkuszu.
•	Webhook / HTTP Request: Integracja z dowolnym zewnętrznym systemem CRM, sklepem internetowym lub aplikacją webową.
•	Schedule Trigger: Cykliczne sprawdzanie bazy danych o określonych godzinach.
•	Inne integracje: Zapier, Typeform, PostgreSQL, CRM (HubSpot, Pipedrive itp.).
🛠️ Architektura i Przepływ Procesu (Workflow)
	1.	Trigger: Wykrycie zdarzenia (Gmail / Google Sheets / Webhook HTTP).
	2.	Twilio: Generowanie i wysyłka wiadomości SMS z unikalnym linkiem do formularza.
	3.	n8n Form Submission: Pr przechwycenie odpowiedzi klienta wraz z danymi ukrytymi (imie, nazwisko, telefon, data_wizyty).
	4.	Switch Node:
•	4–5★ (Pozytywna): Bezpośredni zapis do Google Sheets + strona podziękowania.
•	1–3★ (Negatywna): Przekierowanie do formularza szczegółowego opisu problemu.
	5.	OpenAI (GPT): Analiza tekstu, wyciągnięcie pilności, kategoryzacja i propozycja odpowiedzi.
	6.	Google Sheets: Zapis kompletu danych ze statusem 🔴 Nowe.
	7.	Telegram: Alert do zespołu z podsumowaniem i opcją zmiany statusu.
⚙️ Wymagania i Konfiguracja
	1.	Instancja n8n (Cloud lub Self-hosted).
	2.	Konta API / Usługi:
•	OpenAI API Key
•	Twilio Account SID & Auth Token
•	Telegram Bot Token
•	Google Workspace (Google Sheets API)
	3.	Krok po kroku:
•	Zaimportuj plik .json z przepływem do n8n.
•	Połącz swoje poświadczenia (Credentials) dla Google, OpenAI, Twilio i Telegrama.
•	Stwórz plik w Google Sheets z odpowiednimi kolumnami i regułą sprawdzania danych dla pola Status.
•	Aktywuj dedykowany workflow do obsługi błędów (Error Trigger) i wskaż go w ustawieniach głównego przepływu.
