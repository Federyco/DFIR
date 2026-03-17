https://tryhackme.com/room/unattended [Completado]

![[Pasted image 20260311183125.png]]

https://tryhackme.com/room/disgruntled [Completado]

![[Pasted image 20260311183144.png]]

https://tryhackme.com/room/critical [No Completado]

![[Pasted image 20260311183204.png]]

https://tryhackme.com/room/registry4n6 [No Completado]

![[Pasted image 20260311183232.png]]

https://tryhackme.com/room/caseb4dm755 [No Completado]

![[Pasted image 20260311183257.png]]

- https://tryhackme.com/room/phishingemails1tryoe [Completado]

![[Pasted image 20260314112645.png]]

![[Pasted image 20260316120741.png]]
![[Pasted image 20260316120749.png]]
![[Pasted image 20260316120757.png]]
![[Pasted image 20260316120803.png]]
[EXTRA INFO](https://help.dreamhost.com/hc/en-us/articles/214918038-Email-client-configuration-overview)

[EXTRA INFO](https://web.archive.org/web/20221219232959/https://mediatemple.net/community/products/all/204643950/understanding-an-email-header)


para decodificar un pdf desde base64 linux

grep -E '^[A-Za-z0-9+/=]+$' archivo.txt | base64 -d > file.pdf


- https://tryhackme.com/room/phishingemails3tryoe [Completado]

![[Pasted image 20260314112620.png]]

![[Pasted image 20260316124342.png]]

![[Pasted image 20260316124352.png]]

![[Pasted image 20260316124401.png]]

[Documentation 1](https://csrc.nist.gov/glossary/term/mail_transfer_agent)
[Documentation 2](https://csrc.nist.gov/glossary/term/mail_user_agent)

![[Pasted image 20260316124448.png]]

![[Pasted image 20260316124459.png]]

![[Pasted image 20260316124510.png]]


![[Pasted image 20260316125528.png]]

![[Pasted image 20260316125537.png]]
![[Pasted image 20260316125552.png]]

![[Pasted image 20260316125618.png]]

![[Pasted image 20260316125626.png]]

![[Pasted image 20260316125715.png]]

![[Pasted image 20260316125723.png]]


![[Pasted image 20260316125732.png]]

![[Pasted image 20260316125758.png]]

![[Pasted image 20260316125808.png]]
![[Pasted image 20260316125817.png]]
![[Pasted image 20260316125823.png]]
![[Pasted image 20260316125828.png]]
![[Pasted image 20260316125834.png]]
![[Pasted image 20260316125842.png]]
![[Pasted image 20260316125849.png]]
![[Pasted image 20260316125859.png]]
![[Pasted image 20260316125907.png]]
![[Pasted image 20260316125915.png]]
![[Pasted image 20260316125922.png]]



- https://tryhackme.com/room/boogeyman1 [Completado]

![[Pasted image 20260314112556.png]]

Una de las tareas requiere extraer los dominios de una archivo .json, este filtro hace el trabajito
jq -r '.ScriptBlockText' powershell.json | grep -Eo '([a-zA-Z0-9.-]+\.[a-zA-Z]{2,})'


Query importante cat <archivo_json_powershell> | jq -s -c 'sort_by(.Timestamp) | .[]'| jq '{ScriptBlockText}'| sort | uniq | grep -e 'sq3.exe' -e 'cd'


## Analisys Data

Domains: cdn.bpakcaging.xyz and files.bpakcaging.xyz

Destination_ip: 167.71.211.113

host system: based on python

paquete interesante: 44459

follow tcp stream -> retorna que el stream number es 749

al pasar al stream siguiente, obtenemos un código ASCII

![[Pasted image 20260316224206.png]]que podemos convertir a texto utilizando cualquier herramienta, y obtenemos:

\id=868150bd-a564-423b-9256-70d3781794b1 Master Password
\id=ad8b52f0-e1bb-40f6-bbf9-47a53f9180ab **%p9^3!lL^Mz47E2GaT^y**|ManagedPosition=DeviceId:\\?\DISPLAY#Default_Monitor#1&31c5ecd4&0&UID256#{e6f07b5f-ee97-4a90-b076-33f57bf4eaa7};Position=1106,43;Size=320,320|1|0||Yellow|0||||||0||8ca22c0e-ba5e-499a-a86c-7473a53dc6de|74f08724-ccc9-4ce6-94e7-8c99e6cd42c6|638092247397199589||638092247516107079


ahora finalmente nos solicitan obtener los datos que se encuentran dentro del archivo.

utilizando tshark obtenemos el dato con la query: tshark -r capture.pcapng -Y 'dns' -T fields -e dns.qry.name | grep ".bpakcaging.xyz"

















- https://tryhackme.com/room/boogeyman2 [No Completado]

![[Pasted image 20260314112524.png]]