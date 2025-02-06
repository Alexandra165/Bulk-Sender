  Bulk Sender

  Project Description  
  Bulk Sender is a web application for sending bulk messages via WhatsApp API.  
  It is built using **Golang** for the backend and **Bootstrap, JavaScript, HTML/CSS** for the frontend.  
  The system includes **client management, authentication, and message tracking**.  

  Technologies  
- Backend: Golang, Gin framework  
- Frontend: Bootstrap, JavaScript, HTML, CSS  
- Database: MySQL  
- Integrations: WhatsApp API, Telegram Bot API  
- Authentication: JWT, password hashing  

  Features  
- Web-based interface for sending messages  
- WhatsApp API integration  
- Client management (phone numbers, emails)  
- JWT-based authentication  
- Telegram bot notifications  
- Logging of sent messages  

  Example Code  
  This function sends a message via WhatsApp API:

```go
package main

import (
	"bytes"
	"encoding/json"
	"fmt"
	"log"
	"net/http"
)

// sendMessageToClient sends a message to a specified phone number via WhatsApp API.
func sendMessageToClient(phoneNumber, message string) {
	apiURL := "http://192.168.33.29:7776/send-message"

	data := map[string]string{
		"phone_number": phoneNumber,
		"message":      message,
	}

	jsonData, err := json.Marshal(data)
	if err != nil {
		log.Println("Error encoding JSON:", err)
		return
	}

	resp, err := http.Post(apiURL, "application/json", bytes.NewBuffer(jsonData))
	if err != nil {
		log.Println("Error sending request:", err)
		return
	}
	defer resp.Body.Close()

	fmt.Println("Message sent successfully to:", phoneNumber)
}


```
How to Run
Install Golang: https://golang.org
Clone the repository:
bash

git clone https://github.com/Alexandra165/bulk-sender.git

Configure the MySQL database (if needed).
Install dependencies and start the server:

go mod tidy  
go run main.go  
Open http://localhost:8081 in your browser to access the web interface.
