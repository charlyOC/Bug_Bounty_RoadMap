XSS: 

essayer d’abord une balise simple script ou html.

Si il y a des filtres de baliser essayer ce genre de payload:


surligné = le payload ajouté sur BURP SUITE repeater

		                                    	—------------------------------------------------------
paylopad pas mal quand les event handlers et attributs href sont sont boqués,


à mettre directement dans l’url, le voici non encodé: 

<svg>
<a>
<animate attributeName=href values=javascript:alert(1) />
<text x=20 y=20>Click me</text>
</a> 

                                        	—------------------------------------------------------

pour un lab particulier j’ai utilisé une liste de payload: https://github.com/payloadbox/xss-payload-list/blob/master/Intruder/xss-payload-list.txt

que j’ai mis dans burp intruder, j’ai checké les seuls status 200 et essayé directement dans la webApp, attention aux nombres de requêtes ? 