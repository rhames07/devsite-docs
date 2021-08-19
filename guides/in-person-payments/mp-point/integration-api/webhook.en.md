---
sites_supported:
  - mla
  - mlb
  - mlm
---

## Ejemplos de implementación del algoritmo HMAC-SHA256

Puedes desarrollar el sistema webhook en el lenguaje de programación de tu preferencia, para ello es necesario implementar
una única URL que de respuesta a las peticiones `HTTP GET` para la validación del webhook y `HTTP POST` para la recepción de las notificaciones.

## Implementación HTTP GET - Validación de seguridad.

Para implementar el sistema receptor de notificaciones webhook, es necesario
implementar el algoritmo **HMAC-SHA256** para dar respuesta a la petición HTTP GET
con el `challengeCode` encriptado en formato hexadecimal.

A continuación se muestran snippets de la implementación del algoritmo de cifrado en Go, JAVA y Javascript.

## Ejemplo de la implementación HTTP GET - Validación de seguridad.

```java
import javax.crypto.Mac;
import javax.crypto.spec.SecretKeySpec;
import java.math.BigInteger;
import java.nio.charset.StandardCharsets;

public class Main {
    static String SECRET = "YOUR_TOKEN";
    static String CHALLENGE_CODE = "YOUR_CHALLENGE_CODE";

    static String GetEncryptedChallenge(byte[] secret, byte[] challengeCode) {
        try {
            Mac mac = Mac.getInstance("HmacSHA256"); // Returns a Mac object that implements the specified MAC algorithm
            SecretKeySpec secretKeySpec =
                    new SecretKeySpec(secret, "HmacSHA256"); // Constructs a secret key from the given byte array
            mac.init(secretKeySpec); // Initializes this Mac object with the given key
            byte[] hmacSha256 =
                    mac.doFinal(challengeCode); // Processes the given array of bytes and finishes the MAC operation
            return String.format("%064x", new BigInteger(1, hmacSha256)); // Return the HEX String value
        } catch (Exception e) {
            throw new RuntimeException("Failed to calculate hmac-sha256", e);
        }
    }

    public static void main(String[] args) {
        String encryptedChallenge = GetEncryptedChallenge(SECRET.getBytes(StandardCharsets.UTF_8),
                CHALLENGE_CODE.getBytes(StandardCharsets.UTF_8));
                
        // you can return this encrypted challenge on the response body
        System.out.println("encrypted_challenge: " + encryptedChallenge);
    }
}
```
```go
func webhookGetHandler(w http.ResponseWriter, r *http.Request){

  // Get the challengeCode from the query param
	query, ok := r.URL.Query()["challengeCode"]
	
	if ok {
		challengeCode := query[0]
		
		//encrypt the challengeCode using your token
		sig := hmac.New(sha256.New, []byte(token))
		sig.Write([]byte(challengeCode))
		
		// construct the response body with the encrypted_challenge
		model := IntegratorChallengeResponse{
			EncryptedChallenge: hex.EncodeToString(sig.Sum(nil)),
		}
		jsonBytes, err := json.Marshal(model)
		
		if err != nil {
			w.WriteHeader(http.StatusInternalServerError)
			w.Write([]byte(err.Error()))
		}

		w.Header().Add("content-type", "application/json")
		w.WriteHeader(http.StatusOK)
		
		// return the encrypted_challenge in hex format
		w.Write(jsonBytes)
		
	} else {
		fmt.Printf("\t::fail\n")
		w.Header().Add("content-type", "application/json")
		w.WriteHeader(http.StatusInternalServerError)
		w.Write([]byte{})
	}
}
```
```javascript

// npm install crypto-js

var CryptoJS = require('crypto-js')

const SECRET = 'YOUR_TOKEN';
const CHALLENGE_CODE = 'YOUR_CHALLENGE_CODE';

function GetEncryptedChallenge(secret, challengeCode){

	//encrypt the challengeCode using your token
	const hash = CryptoJS.HmacSHA256(challengeCode, secret);
	const HexHash = CryptoJS.enc.Hex.stringify(hash);
	return HexHash;
}

var encryptedChallenge = GetEncryptedChallenge(SECRET, CHALLENGE_CODE);

// you can return this encrypted challenge on the response body
console.log("encrypted_challenge: ", encryptedChallenge);
```

  
## Ejemplo de la implementación HTTP POST - recepción de notificaciones  (Golang).

``` Go 
func webhookPostHandler(w http.ResponseWriter, r *http.Request){
	fmt.Printf("::webhook:callback\n")
	bodyBytes, _ := ioutil.ReadAll(r.Body)
	defer r.Body.Close()
	fmt.Printf(string(bodyBytes) )
	fmt.Printf("\n\t::response: 200\n")
	fmt.Printf("=================================================================\n")
	w.Header().Add("content-type", "application/json")
	w.WriteHeader(http.StatusOK)
}
```
