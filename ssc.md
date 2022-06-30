

**DI - Sign= ador Centralitzat (SSC)**

<= /p>

Realitzat per: Consorci AOC –= Servei Eines de Signa= tura

Versió: 1.3.3

Fecha: 30/= 06/2022  

  

                                                 =                                           

                                                 =                                           

  

**Control del** **document**

**Informació** **general**

**Título:**

GuiaIntegracioSSC.v1.3.3.docx

**Creat** **per:**

Consorci AOC= – Servei Eines de Signatu= ra

**Nom** **del documento:**

<= /span><= span lang=3DEN-US style=3D'mso-bidi-font-size:10.0pt;font-family:"Calibri",san= s-serif; mso-bidi-font-family:"Times New Roman";mso-ansi-language:EN-US;mso-no-pro= of: yes'>GuiaIntegracioSSC.v1.3.3.docx<= /span>

**Histórico de revisiones**

**Versió**

**Data**

**Autor**

**Comentaris**

1.3.2

26/10/2016

Servei Eiunes de Signatura

\= Actualització\= de contingut.

 <= /o:p>

 <= /o:p>

  

Index

[1           Introducció. 4](3D"#_Toc483913121")<= /span><= /span>

[2           URLS de l’SSC. 5](3D"#_Toc483913122")<= /span><= /span>

[2.1     PREPRODUCCIÓ.. 5](3D"#_Toc483913123")<= /span>

[2.2     PRODUCCIÓ.. 5](3D"#_Toc483913124")<= /span>

[2.3     Connexió. 5](3D"#_Toc483913125")<= /span>

[2.3.1 Habilitar la propietat de JVM.. 6](3D"#_Toc483913126")<= /span>

[2.3.2 Habilitar la propietat com a variable d’entorn. 6](3D"#_Toc483913127")<= /span>

[3           SmartWrapper 7](3D"#_Toc483913128")<= /span><= /span>

[3.1     L’API SmartWrapper 7](3D"#_Toc483913129")<= /span>

[3.2     Accés a l’SSC mitjançant SmartWrapper 7](3D"#_Toc483913130")<= /span>

[3.3     Classes de l’API SmartWrapper 8](3D"#_Toc483913131")<= /span>

[3.3.1 Classe per gestionar peticions SmartWrapper de signatura. 8](3D"#_Toc483913132")<= /span>

[3.3.2 Classe per gestionar respostes SmartWrapper de signatura. 8](3D"#_Toc483913133")<= /span>

[3.3.3 Classe SmartHeader per gestionar la capçalera. 8](3D"#_Toc483913134")<= /span>

[3.3.4 Classe Constants per gestionar constants<= span style=3D'color:windowtext;display:none;mso-hide:screen;mso-no-proof:yes; text-decoration:none;text-underline:none'>.](3D"#_Toc483913135") [8](3D"#_Toc483913135")<= /span>

[3.4     Configuració d’SmartWrapper 9](3D"#_Toc483913136")<= /span>

[3.4.1 JDK\= . 9](3D"#_Toc483913137")<= /span>

[3.4.2 Llibreries del client 9](3D"#_Toc483913138")<= /span>

[3.5     Arxiu smartwrapper.properties. 9](3D"#_Toc483913139")<= /span>

[4           Serveis de Signatura. 11](3D"#_Toc483913140")<= /span><= /span>

[4.1     Signatura CMS attached. 11](3D"#_Toc483913141")<= /span>

[4.2     Signatura XML enveloped. 13](3D"#_Toc483913142")<= /span>

[4.3     Signatura XAdES-T detached a partir del hash d’un document 15](3D"#_Toc483913143")<= /span>

[4.4     Signatura de documents PDF. 16](3D"#_Toc483913144")<= /span>

[4.4.1 Paràmetres de signatura visible. 19](3D"#_Toc483913145")<= /span>

[5           Gestió de dades de volum gran. 29](3D"#_Toc483913146")<= /span><= /span>

[5.1     Gestió de peticions amb dades de gran tamany. 29](3D"#_Toc483913147")<= /span>

[5.2     Gestió de respostes amb dades de gran tamany. 30](3D"#_Toc483913148")<= /span>

[5.3     Exemple de gestió en arxius per generació d’una signatura XAdES-BES enveloping. 31](3D"#_Toc483913149")<= /span>

[6           Exemple d’ús amb SoapUI 32](3D"#_Toc483913150")<= /span><= /span>

[6.1     Importar un projecte. 32](3D"#_Toc483913151")<= /span>

[6.2     Afegir certificat PKCS#12. 32](3D"#_Toc483913152")<= /span>

  

1&nb= sp;      Introducció
==========================

El Signador Centralitzat és la solució que dóna cobertura al concepte de sistema de signatura electrònica per a l’actuació administrativa automatitzada, tal com es descriu a la LAECSP (art.18, Llei 11/2007). Permet la custòdia i ús posterior de segells electrònics de les administracions públiques, òrgans o entitats de dret públic de Catalunya qu= e ho sol·licitin, agilitzant la posada en marxa d’un sistema automatitzat de signatura electrònica de documents des d’un dispositiu remot. En aquesta UR= L es pot consultar la informació del servei : [https://www.aoc.cat/servei= s-aoc/signador-centralitzat/](3D"https://www.aoc.cat/serveis-aoc/signador-centralitzat/") \=

Les claus associades al segell electrònic, resideixen en magatzems de c= laus protegits per un dispositiu criptogràfic segur (HSM). El dispositiu està certificat sota els criteris de Common Critera EAL4+, oferint les màximes garanties en matèr= ia de seguretat i custòdia de claus.

La guia bàsica d’integració al Servei de Signatura Cen= tralitzada (SSC) és un document que va dirigit a desenvolupadors<= /span> que vulguin integrar les s= eves aplicacions de gestió amb l’SSC de l’AOC.

El le= ctor d’aquest document ha de s= er un professional amb coneixements en programació avançada en el llenguatge\= Java. És molt recomanable disposar també de coneixem= ent sobre Webservices, missatg= eria SOAP, WS-Security, ús de c= ertificats i signatures digitals.

L’objectiu d’aquest document és oferir una guia bàsica d’integració amb l’SSC mitjançant tecnologia Java

La disposició de capitols és la següent:\=

Al capítol 2 s’indiquen les U= RLs d’accés als Webservices de signatura de l’SS= C. Al capítol 3 es descriu l’= SmartWrapper, API d’integració a l’SSC. Al capítol 4 es descriu com accedir als serveis de creació de signatura mi= tjançant SmartWrapper, amb <= span class=3DSpellE>codi d’exemple. També s’indica com parametritzar la signatura visible de documents PDF. Finalment, al capítol 5 es descr= iu la gestió de dades de gran volum amb l’API SmartWrapper

L’accés al servei es fa mitjançant canal segur SSL amb autenticació de client. Les següent són les URLs per accedir al Servei de Signatura Centralitzad= a pels entorns de PREPRODUCCIÓ i PRODUCCIÓ.

                                                 =                                                                            =                               

2&nb= sp;      URLS de l= ’SSC
==============================

L’accés al servei es fa mitjançant canal segur SSL amb autenticació de client. L= es següent són les URLs per accedir al Servei de Signatura Centralitzad= a pels entorns de PREPRODUCCIÓ i PRODUCCIÓ.

2.1&= nbsp;     PREPRODUCCIÓ
----------------------------

La URL d’accés al Webservice<= /span> de signatura de l’SSC a l’= entorn de PREPRODUCCIÓ mitjançant certificat és:

[https://ssc.preproduccio.catcert.ca= t:8443/trustedx-sgw/SignCert](3D"https://ssc.preproduccio.catcert.cat:8443/trustedx-sgw/SignCert")

2.2&= nbsp;     PRODUCCIÓ<= /h2>

La URL d’accés al Webservice<= /span> de signatura de l’SSC a l’= entorn de PRODUCCIÓ mitjançant ce= rtificat és:

[https://ssc.catcert.cat:8443/truste= dx-sgw/SignCert](3D"https://ssc.catcert.cat:8443/trustedx-sgw/SignCert")


---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

2.3&= nbsp;     Connexió
------------------------

Els protocols utilitzats per realitzar = les connexions SSL depenen de= la versió de Java amb la qual s'executa l'aplicació. Per defect <= span class=3DSpellE>SmartWrapper utilitza protocols segurs per xifrar la comunicació amb el servidor utilitzant TLS amb la versió 1.1 o 1.2. = D'altra banda, les versions de TLS per defecte que s'util= itzen en cada versió de Java var= ien, tal com mostra la <= span class=3DSpellE>següent taula:

Per tal motiu, per a versions anteriors de Java 1.7.XX cal habilitar l'ús de TLSv1.0 per a= realitzar les comunicacions SSL. Hi ha dues formes d’habili= tar aquest protocol, mitjançant una variable global al sistema o amb una variable a la màquina virtual de Java (JVM).

  

\=  

### 2.3.1       Habilitar la p= ropietat de JVM<= /span>

Abans de fer\= la connexió amb TrustedX (mètode send) cal introdui= r el següent codi:

System.setProperty("PropertyAllowTl= s10AsClient", "true");

Aquesta propietat habilitarà l'ús de TLSv1.= 0 a la màquina virtual de Java per a l'= aplicació de SmartWrapper.

### 2.3.2       Habilitar la p= ropietat \= com a variable d’entorn

Depenent del sistema operatiu, la configuració de variables \= d’entorn difereix. Cal afegir la variable d’entorn PropertyAllowTls10AsClient amb valor <= /span>true.

\=  

2.4&= nbsp;      
-----------------

3      = S= martWrapper
=======================

En aquest capítol <= span class=3DSpellE>oferim una versió general= de l’API SmartWrapper propor= cionada per accedir a l’SSC\= .

3.1      L’API SmartWrapper
---------------------------

SmartWrapper és una API desenvolupada = sobre Axis per crear aplicacions client sense necessitat d’aprofundir en la complexitat d’Axis (permet també l’accés a estructures Axis d’ús<= /span> avançat). SmartWrapper permet generar aplicacions Java senzilles, i amb poques <= span class=3DSpellE>línies de codi.

3.2      A= ccés a l’SSC mitjançant SmartWrapper
------------------------------------------------

A continuació resumim els passos necessaris per enviar una \= petició a l’SSC, obtenir la= resposta i consultar si s’ha processat correctament.

Per invocar el servei i avaluar la resposta:

1.&n= bsp;     Creem= una instància de la classe= SmartSig= nRequest corresponent al servei invocat.

2.&n= bsp;     Recup= erem l’objecte Stub de l= a classe Axis mitjançant el= mètode getStub.

3.      Utilitzem\= el mètode setHeader per a l’objecte Stub afegint els tags (Rol i Dispositari).

4.&n= bsp;     Creem= una instància de la classe= Request<= /span> corresponent al servei invocat.

5.&n= bsp;     Reali= tzem les operacions set necessà= ries per construir una petició \= vàlida.

**Important**: A la petició hem de d= efinir tant el perfil escollit (= mitjançant el mètode setProfi= le) com els paràmetres adequats a aquell p= erfil.

6.&n= bsp;     Envie= m la petició (mitjançant\= la operació send) per= obtenir un objecte del tipus Response.

7.&n= bsp;     Consu= ltem, mitjançant els mètodes de l’objecte Response, el = resultat de la petició. S= i la petició ha sigut processada correctament, = obtenim el valor dels paràmetres retornats amb les mètodes get del mateix objecte Response.

  

\=  

3.3      C= lasses de l’API SmartWrapper
----------------------------------------

En aquest punt descrivim les classes utilitzades per l’API SmartWrapper.=

### 3.3.1=       = C= lasse per gestionar peticions SmartWrapper de signatura

La classe de l’API SmartWrapper que serveix per gestionar peticions<= /span> de signatura, és la següen= t:

o   <= /span>Serveis de signatura digital: SmartSignRequest

Aquest classe inclou els següents mètodes:

o   <= /span>Mètode send per = enviar la petició. Aquest = mètode retorna un objecte\= de la classe associada amb la resposta corresponent.

o   <= /span>Mètodes per assignar valors als paràmetres necessaris en cada petició= . Els noms d’aquests mètodes segueixen la sintaxi set<P= aram\>, on <Param\> és el nom del paràmetre al que = assignen valor (amb la pr= imera lletra en majúscules).

### 3.3.2=       = C= lasse per gestionar respostes SmartWrapper de signatura

La classe de l’API SmartWrapper per ge= stionar respostes de signatura, és la següent:

o   <= /span>Serveis de signatura digital: SmartSignResponse

Aquesta classe inclou mètodes per consultar els paràmetr= es de la resposta. Els\= noms d’aquests mètodes segueixen la sintaxi get<Param&g= t;, on <Param\> és el nom del paràmetre el valo= r del qual es vol consultar (amb la primera lletra en = majúscules).

### 3.3.3=       = C= lasse \= SmartHeader per gestionar la capçalera

La classe SmartHea= der gestiona la capçalera de les peticions i inclou informació\= per la correcta autenticació al s= ervei. En concret, suporta autent= icació amb certificat.

Tanmateix, l’autenticació la portarem a terme sempre mitjançant certificat digital per l’a= plicació en concret que vol = consumir els serveis de l’SSC.

Cal emfatitzar que = el servei inclou dos paràmetres nous a la capçalera: _Ro= l_ i _Dispositari_. Ambdós elements son presents al fitxer de propietats.

### 3.3.4=       = C= lasse \= Constants per gestionar constants

La classe Constant= s defineix una sèrie de constants per facilitar l’ús de l’API i reduir el risc d’error tipogràfics.

3.4      C= onfiguració \= d’SmartWrapper
-----------------------------------------

### 3.4.1=       = JDK

El sistema on s’executin ha de tenir instal•lada la **Java JDK1.4 (o superior).**

### 3.4.2=       = L= libreries del client

Les llibreries necessàries pel correcte = funcionament del client <= span class=3DSpellE>basat en SmartWrapper són:

o   <= /span>smartwrapper.jar

o&nb= sp;  trustedx-client-axis-stub.jar

o&nb= sp;  trustedx-client-axis.jar

o&nb= sp;  trustedx-provider.jar

o&nb= sp;  activation.jar

o   <= /span>axis.jar

Durant la compilació, aquest arxiu només és necessari per co= dificar i descodificar valors en Base64 mitjançant la classe org.apache\= .axis.encoding.Base64.

o   <= /span>commons-discovery-0.2.jar

o&nb= sp;  commons-httpclient-3.0.1.jar<= /p>

o&nb= sp;  commons-logging-1.0.4.jar

o&nb= sp;  jaxrpc.jar

o&nb= sp;  log4j-1.2.8.jar

o&nb= sp;  saaj.jar

o&nb= sp;  wsdl4j-1.5.1.jar

o&nb= sp;  xercesImpl.jar

o&nb= sp;  xml-apis.jar

o&nb= sp;  commons-collections-3.2.jar

o&nb= sp;  commons-configuration.jar

o&nb= sp;  commons-lang-2.6.jar

o   <= /span>sfly-ssl.jar

3.5      A= rxiu \= smartwrapper.properties
-------------------------------------------

El directori des d’on s’executi el client, haurà d’incloure l’arxiu de configuració **smartwrapper.properties**.

La següent taula defineix els paràmetres inclosos en l’arxiu\= smartwrapper.properties:

Paràmetre

Valor

<= span lang=3DES style=3D'font-size:10.0pt;mso-bidi-font-size:11.0pt'>Truststore= .active

true: per la connexió HTTP es farà servir el magatzem\= de certificats definit al = paràmetre Truststore.path.

false (valor por defecte): s’utilitzarà el magatzem de certificats configurat = en la màquina virtual de Java (si n’= hi ha).

Truststore.path

Magatzem de certificats que s’utilitzarà a la co= nnexió HTTP (si el valor de Truststore.active és true).

Comptabilitzada l’obligació reconeguda

Contrasenya del magatzem de certificats definit a Truststore.path.

Pagada

true: per la connexió HTTPS s’utilitzarà el magatzem de claus definit al paràmetre Keystore.path\= .

false (valor por defecte): s’utilitzarà el magatzem de claus configurat en a <= span class=3DSpellE>màquina virtual de Java (si n’= hi ha).

Keystore.p= ath

Magatzem de claus utilitzat en la <= span class=3DSpellE>connexió HTTPS (si el valor de keystore.active és true).

Keystore.<= span class=3DGramE>password

Contrasenya del magatzem de claus definit a Keystore.path\= .

Keystore.T= ype

Tipus de keystore: JKS (valor per defec= te), JCEKS, o PKCS12

Proxy.acti= ve

true: per la = connexió HTTP s’utilitzarà un servidor Proxy.

false: no s’utilitzarà un servidor proxy.

Proxy.host=

Servidor prox= y utilitzat (si proxy.active és true).

Proxy.port=

Port del serv= idor proxy.

Proxy.user= name

Nom d’usuari per accedir al servidor proxy (si requereix autenticació HTTP bàsica).

Proxy.password

Contrasenya per accedir al servidor proxy (si \= requereix autenticació HTTP bàsica= ).

Timeout

Temps d’espera de la connexió\= HTTP (en mil·lisegons).

Request.lo= adPath

Directori base dels arxius creats per enviar amb les petic= ions quan es maneguen = dades de gran tamany.

Response.s= avePath

Directori base dels arxius creats en rebre les respostes quan es maneguen dades = de gran tamany.

req-log.active

true: las peticions SOAP enviades es guardaran en arxius de log.

false (valor = por defecte): les peticions\= SOAP enviades no es guardaran en arxius de log.

req-log.savePath

Directori on es guardaran els arxius de log amb les <= span class=3DSpellE>peticions enviades

(si el valor de req-<= span class=3DGramE>log.active és tru= e).

res-log.active

true: es guar= daran arxius de log amb\= el contingut de les respostes rebudes.

false (valor = por defecte): no se guardaran arxius de log amb el contingut de les respostes rebudes.

res-log.savePath

Directori on es guardaran els arxius de log amb les <= span class=3DSpellE>respostes rebudes \=

(si el valor = de res-log.active és true).

authN.poli= cy

Política d’autenticació sol·licitada (opcional).

Ssl.allowC= riticalExts

true: durant la connexió SSL = es permeten certificats de servidor amb qualsevol extensió marcada com a = crítica.

false (valor = per defecte): durant la connexió SSL no es permeten certificats de servidor amb extensions crítiques.

Ssl.noVali= dation

true: s’anul·la la validació = del certificat del servidor durant= les connexions SSL.

false (valor = per defecte): es valida el = certificat del servidor durant= les connexions SSL.

Ssl.valida= tion

Algorisme per validar = el certificat del servidor durant= connexions SSL. L’algorisme utilitzat ha d’estar implementat per un proveïdor criptogràfic registrat.=

4      = Serveis de Signatura
=============================

En aquest capítol <= span class=3DSpellE>explicarem, fent ús de casos pràctics, com accedir als serveis de creació = de signatura mitjançant Smart= Wrapper.

En tots aquests exemples farem servir l’autenticació de client mitjançant certificat. A tal efecte,= caldrà configurar l’arxiu\= smartwrapper.properties amb les dades del keystore i el truststore. Pels exemples farem servir el = keystore i el truststore = de proves que distribuïm dins el pack d’integració\= :

 \=

\# t= ruststore

<= span lang=3DEN-GB style=3D'mso-bidi-font-size:10.0pt;font-family:"Courier New"; mso-ansi-language:EN-GB;mso-fareast-language:CA'>Truststore.active =3D true

<= span lang=3DEN-GB style=3D'mso-bidi-font-size:10.0pt;font-family:"Courier New"; mso-ansi-language:EN-GB;mso-fareast-language:CA'>Truststore.path =3D resources/truststore/catcert.truststore

<= span lang=3DEN-GB style=3D'mso-bidi-font-size:10.0pt;font-family:"Courier New"; mso-ansi-language:EN-GB;mso-fareast-language:CA'>Truststore.password\= \=3D \= catcert

\# keystore

<= span lang=3DEN-GB style=3D'mso-bidi-font-size:10.0pt;font-family:"Courier New"; mso-ansi-language:EN-GB;mso-fareast-language:CA'>Keystore.active =3D true

<= span lang=3DEN-GB style=3D'mso-bidi-font-size:10.0pt;font-family:"Courier New"; mso-ansi-language:EN-GB;mso-fareast-language:CA'>Keystore.path =3D resources/keystore/apptest/20100428\_111540\_CDA\_1\_cda\_c1\_policy.p12

<= span lang=3DES style=3D'mso-bidi-font-size:10.0pt;font-family:"Courier New";mso-= fareast-language: CA'>Keystore.password =3D 1234

<= span lang=3DES style=3D'mso-bidi-font-size:10.0pt;font-family:"Courier New";mso-= fareast-language: CA'>Keystore.type =3D PKCS12

4.1      Signatura CMS attached
-------------------------------

Amb el c= odi següent enviem una = petició SOAP de creació <= span class=3DSpellE>d’una signatura CMS attached (adjunta), i consultem la \= resposta obtinguda.

 \=

import com.safelayer.trustedx.client.smartwrapper.\*; <= o:p>

import org= .apache.axis.encoding.Base64;

import org.apache.axis.message.SOAPHeaderElement;\=

public class CmsSignature {

       static final String _TRUSTEDX\_URL_ =3D "https://ssc.preproduccio.catcert.cat:8443/trustedx-sgw/SignCert";

       static final String _SIGNER\_DN_ =3D "CN=3DDum= my";

       static final String _RESULTMAJOR\_SUCCESS_ =3D &quo= t;urn:oasis:names:tc:dss:1.0:resultmajor:Success"; =

       static final String _DIPOSITARI_ =3D "O=3D000= 0000000";

       static final String _ROL_  \=3D "TEST";\=

       public static byte\[\] signCms(byte\[\] data= ToSign) throws Exception {

             SmartSig= nRequest sReq =3D new SmartSignRequest(_TRUSTEDX= \_URL_);

             //\= afegeix la capçalera a la petició

             Stub stub =3D (Stub) sReq.getStub();<= /span>

             stub.setHeader(null, "Rol", ROL);

             stub.setHeader(null, "Dipositari", DIPOSITARI);

             //sig= natura CMS

             sReq.set= Profile(Constants.Profile._CMSPKCS__7_);

             //sig= natura attached

             sReq.set= EnvelopingSignature(true);

             //dad= es a signar

             sReq.setInputBase64Data(Base64._encode_(dataToS= ign));

             //selecció de<= /u> la clau de signatura

             sReq.setKeySubjectName(<= i>SIGNER\_DN);

             //enviament de= la petició

             SmartSignResponse sResp =3D sReq.sen= d();

             if (_RESULTMAJOR\_SUCCESS_.equals(sResp.getResultMajor())

                    && sResp.getResultMinor() =3D=3D null) {

                    //recuperació de la signatura

                    String signatureBase64 = =3D sResp.getSignatureBase64();

                    return Base64._decode_(signatureBase64);

             } else {

                    throw new Exception("Error signing:" + sResp.getResultMessage());

             }

       }

       public static void main(String args\[\]) throws Exception {

       String data =3D "data to sign.= ..";

       byte\[\] signature =3D _sig= nCms_(data.getBytes());

       }

}

Per construir la petició, invoquem els mètodes de la classe SmartSig= nRequest i SmartHea= der descrits a la taula següent:

La classe SmartHea= der permet afegir paràmetres al element Header de l= a petició SOAP. Aquesta classe es comporta igual a tots<= /span> els següents exemples.

Mètode

Paràmetres

Mètode

Paràmetres

getStub

Obté l’objecte Stub de baix nivell Axis.

getStub

Obté l’objecte Stub de baix nivell Axis.

setHeader

Afegeix<= span lang=3DEN-GB style=3D'font-size:10.0pt;mso-bidi-font-size:11.0pt;mso-ansi= -language: EN-GB'> l’element al node Header.<= /span>

setHeader

Afegeix<= span lang=3DEN-GB style=3D'font-size:10.0pt;mso-bidi-font-size:11.0pt;mso-ansi= -language: EN-GB'> l’element al node Header.<= /span>

D’altra band= a, la classe SmartSignRequest construeix l’element Body de la petició SOAP.

Mètode

Paràmetres

setProfile <= /p>

Constants.Profile.CMSPKCS7 per sele= ccionar el tipus de signatura CMS/PKCS#7.<= /span>

setEnvelopingSignature <= /p>

true per signatura attached (adjunta).

setInputBase64Data

Dades a signar, codificades en Base64.

Amb els<= /span> mètodes de la classe SmartSig= nResponse obtenim la resposta a la = nostra petició de signatu= ra:

Mètode

Paràmetres

getResultMajor 

Indica si s’ha p= ogut processar la petició, independentment del resultat d’aquesta.

getResultMinor <= /p>

Detalls de la operació.

getSignatureBase64  \=

Signatura CMS codificada en Base64.

 
-

  

\=  

4.2&= nbsp;     Signatura XML e= nveloped
-----------------------------------------

Amb el c= odi següent enviem una = petició SOAP de creació <= span class=3DSpellE>d’una signatura XML enveloped (embolcallada), i consultem la resposta obtinguda.<= /o:p>

import com.safelayer.trustedx.client.smartwrapper.\*; <= o:p>

import org= .apache.axis.encoding.Base64;

import org.apache.axis.message.SOAPHeaderElement;

public class XmlEnvelopedSignature {

       static final String _TRUSTEDX\_URL_ =3D "https://ssc.preproduccio.catcert.cat:8443/trustedx-sgw/SignCert";

       static final String _SIGNER\_DN_ =3D "CN=3DDum= my";

       static final String _RESULTMAJOR\_SUCCESS_ =3D &quo= t;urn:oasis:names:tc:dss:1.0:resultmajor:Success"; =

       static final String _DIPOSITARI_ =3D "O=3D000= 0000000";

       static final String _ROL_  \=3D "TEST";\=

       public static byte\[\] signEnvelopedXml(byte\[\] data= ToSign) throws Exception {

             SmartSig= nRequest sReq =3D new SmartSignRequest(_TRUSTEDX= \_URL_);

             //\= afegeix la capçalera a la petició

             Stub stub =3D (Stub) sReq.getStub();<= /span>

             stub.setHeader(null, "Rol", ROL);

             stub.setHeader(null, "Dipositari", DIPOSITARI);

             //sig= natura XML simple

             sReq.set= Profile(Constants.Profile._XADES_);

             sReq.set= SignatureFormat(Constants.SignatureFormat._NOADES_);<= /o:p>

             //sig= natura enveloped

          =     sReq.setSignaturePlacement(Constants.SignaturePlacement._ENVELOPED_);

             //\= posicionament de la signatura dins el document

             sReq.setXmlEnvelopedXPathFirstChildOf("/");

             //dad= es a signar

             sReq.setInputXmlBase64(Base64= ._encode_(dataToSign)); <= /span>

             //\= selecció de la clau de si= gnatura

             sReq.setKeySubjectName(<= i>SIGNER\_DN);

             //enviament de= la petició

             SmartSignResponse sResp =3D sReq.sen= d();

             if (_RESULTMAJOR\_SUCCESS_.equals(sResp.getResultMajor())

             && sResp.getResultMinor() =3D=3D null) {

                    //recuperació de la signatura

                    String signature =3D sResp.getDocumentWithSignatureXml();

                    return signature.getB= ytes();

             } else {

                    throw new Exception("Error signing:" + sResp.getResultMessage());

             }

       }

       public static void main(String args\[\]) throws Exception {

             String data =3D "<lib= rary Id=3D'c123tpe4ryta6di24'>"

             +"<book Id=3D'1'>&= quot;

             +" <title>The dark house</title>"

             +"</book>"

             +"<book Id=3D'2'>&= quot;

             +" <title>The laundry</title>"

             +"</book>"

             +"</library>";

             byte\[\] signature =3D _signEnvelopedXml_(data.get= Bytes());

             System.<= i>out.println("sig= nature=3D" + new String(signature));

       }

}

Per construir la petició, invoquem els mètodes de la classe SmartSig= nRequest descrits a la taula següent:

Mètode

Paràmetres

setProfile

Constants.Profile.XA= DES per selec= cionar el perfil de signatura XML (tant per signatures simples com = avançades).

setSignatureFormat

Format de la signatura. Pot tenir els següents valors:<= o:p>

Signatura simple:

Constants.SignatureF= ormat.NOADES

Signatura AdES\-BES:\=

Constants.SignatureFormat.BES

Signatura AdES\-T:

Constants.SignatureFormat.ES\_T

Signatura AdES\-C:

Constants.SignatureFormat.ES\_C

Signatura AdES\-A:

Constants.SignatureFormat.ES\_A

setSignaturePlacement

Constants.SignatureP= lacement.ENVELOPED per selec= cionar el tipus de signatura XML enveloped.

Per seleccionar una signatura detached, farem servir el següent\= paràmetre:

Constants.SignatureP= lacement.DETACHED

I per seleccionar una signatura del tipus enveloping, farem servi= r el paràmetre:

Constants.SignatureP= lacement.ENVELOPING

setXmlEnvelopedXPathFirstChildOf\=

Expressió XPath que indica on volem que s’incrusti la signatura generada. Per exemple, "/" per ubicar la signatura a continuació<= /span> del node arrel de= l document XML.

setXmlReturnBase64

true per obtenir la signatura codific= ada en Base64 (i evitar així pr= oblemes amb Axis a l’hora\= de serialitzar i deserialitzar signatures XML).

setKeySubjectName

Certificat amb el que generar la signatura.

setInputXmlBase64

Dades a signar, codificades en Base64.

Amb els<= /span> mètodes de la classe SmartSig= nResponse obtenim la resposta a la = nostra petició de signatu= ra:

Mètode

Paràmetres

getResultMajor 

Indica si s’ha p= ogut processar la petició, independentment del resultat d’aquesta.

getResultMinor <= /p>

Detalls de la operació.

getDocumentWithSignatureXml

Signatura XML.

getDocumentWithSignatureXmlBase64

Signatura XML codificada en Base64.

4.3      Signatura X= AdES\-T detached a partir del hash d’un document
----------------------------------------------------------------------

import com.safelayer.trustedx.client.smartwrapper.= \*;

import org.apac= he.axis.encoding.Base64;

import org.apache.axis.message.SOAPHeaderElement; =

public class XAdESTDetachedSignature = {

       \= static final String _\= TRUSTEDX\_URL_ =3D "https://ssc.preproduccio.catcert.cat:8443/trustedx-sgw/SignCe= rt";

       \= static final String _\= SIGNER\_DN_ =3D "CN=3DDummy";

       \= static final String _\= RESULTMAJOR\_SUCCESS_ =3D "urn:oasis:names:tc:dss:1.0:resultm= ajor:Success";

       \= static final String _\= DIPOSITARI_ =3D "O=3D0000000000";

       \= static final String _ROL_  \=3D "TEST";

       \=

       \= public static byte\[\] signDetachedXAdEST(byte\[\] \= dataToSign) throws Exception {

              =                         

             <= /span>SmartSignRequest sReq\= =3D new SmartSignRequest(_TRUSTEDX\_URL_);

             <= /span>//afegeix la \= capçalera a la petició

             Stub stub =3D (Stub) sReq.getStub();

             stub.setHeader(null, "Rol", ROL);

             stub.setHeader(null, "Dipositari", DIPOSITARI);

             <= /span>//signatura XML simple

             <= /span>sReq.setProfile(Constants.Profile._XADES_);

             <= /span>sReq.setSignatureFormat(Cons= tants.SignatureFormat._ES\_T_);

             <= /span>//dades<= /u> a signar

             <= /span>sReq.setInputHashDigest(data= ToSign.toString());

             <= /span>sReq.setInputHashAlgorithm("sha1");

             <= /span>//selecció de la clau de signatura

             sReq= .setKeySubjectName(_SIGNER\_DN_); <= /span>            

             //enviament de la petició

             SmartSignResponse<= span lang=3DEN-GB style=3D'font-size:9.0pt;mso-bidi-font-size:10.0pt;font-fa= mily: "Courier New";mso-ansi-language:EN-GB'> sResp =3D sReq.send();

             <= /span>if (_\= RESULTMAJOR\_SUCCESS_.equa= ls(sResp.getResultMajor())

             <= /span>&& sResp.getResultMinor() =3D=3D null) {

                    //recuperació de la signatura

                    String signature =3D sRes= p.getSignatureXml();

              =       return \= signature.getBytes();

            } else {

              =       throw new Exception("Error signing:" + <= span class=3DSpellE>sResp.getResultMessage());

             <= /span>}

       \= }

       \=  

       \= public static void main(String args\[\]) throws Exception {

             <= /span>String data =3D "gYbYj9w6DofPvCfwqKKwXitsErA=3D"= ;

             <= /span>byte\[\] signature =3D signDeta= chedXAdEST(data.getBytes());

             <= /span>System.out.println("signature=3D" + new String(signature));

       \= }

} En aquest cas, expo= sem codi d’exemple per = generar una signatura XML avançada amb segell de temps, a = partir del resum criptogràfic (hash) d’un document.

  

\=  

Per construir la petició, invoquem els mètodes:

Mètode

Paràmetres

setInputHashDigest

Hash de les dades a signar, codificat\= en Base64.

setInputHashAlgorithm

Algorisme de hash amb que s’ha calculat el resum anter= ior

4.4      Signatura de documents PDF
-----------------------------------

Amb el codi següent enviem una petició de sig= natura d’un document PDF, fent signatura visible, i consul= tem la resposta obtinguda.

**Important**: L’S= SC només suporta la signatura d’arx= ius PDF que utilitzin la versi= ó 1.5 del format PDF.

import com.safelayer.trustedx.client.smartwrapper.\*;

import java.io.\*;=

import org.apache\= .axis.encoding.Base64;

import org.apache.axis.message.SOAPHeaderElement;

public class PdfSignatu= re {

       static final String TRUSTEDX\_URL =3D "https://ssc.preproduccio.catcert.cat:8443/trustedx-sgw/SignCert";

       static final String SIGNER\_DN =3D "CN=3DDummy";

       static final String RESULTMAJOR\_SUCCESS =3D "urn:oasis:names:tc:dss:1.0:resultmajor:Success";

       static final String DIPOSITARI =3D "O=3D0000000000";=

       static final String ROL  =3D "TEST";

       public static byte\[\] signPdf(byte\[\] pdfToSign, String signatur= eInfo) throws Exception{   

            =    SmartSignRequest sReq =3D= new SmartSignRequest(TRUSTEDX\_URL);

            =    //afegeix la capçalera a la petició

               Stub \= stub =3D (Stub) sReq.getStub();<= /span>

            =    stub.setHeader(null, "= ;Rol", ROL);

            =    stub.setHeader(null, "Dipositari", DIPOSITARI);

               //signatura d’un document PDF

               sReq.setProfil= e(Constants.Profile.PDF);

            =    //tipus de signatura

               sReq.setSignatureType(Constants.SignatureType.CMS);

               //selecció de la clau de signatura

               sReq.setKeySub= jectName(SIGNER\_DN);

            =    //PDF a signar

            =    sReq.setInputPdfBase64Data(Base64.encode(pdfToSign));

               //configuració signatura visible

               sReq.setPdfSignatureInfo(signatureInfo);

               //enviament de la petició

               SmartSignRespo= nse sRes= p =3D sReq.send();

            =   

            =    if (RESULTMAJOR\_SUCCESS.equals(sResp.getResultMajor()) && sResp.getResultMinor() =3D=3D null) = {

            =           return Base64.decode(sResp.getDocumentWithSignaturePdf\= ());

            =    } else {

            =           throw new Exception("Error signing:" + sResp.getResultMessage());

            =    }

       }

       public static void main(String arg= s\[\]) throws Exception {

            =    String signatureInfo =3D

            =    "<css:PdfSignatureInfo xmlns:css\=3D'http://www.safelayer.com/TWS'>" = +

            =    "<css:PdfAttributes\><<= span class=3DSpellE>css:signatureAlg\>SHA1</css= :signatureAlg\>" +

            =    " <css:validationMethod\>PPKMS</css:validationMethod\>" +

            =    " <css:signaturePosition\>ADDLAST</css:signaturePosition\>" + <= /p>

            =    " <css:params\>&l= t;css:reason\>Author</css:rea= son\></css:params\>" +

            =    "</css:PdfAttributes\>"= ; +

            =    "<css:Appearance\>" +=

            =    " <css:Rect x0=3D'1= 00' y0=3D'50' x1=3D'520' y1=3D'150'/>" +

            =    " <css:Background&g= t;<css:image encodeType\=3D'b= ase64'>" +

             "<css:data>/9j/4AAQSkZJRg= ABAQEAYABgAAD/4QAWRXhpZgAASUkqAAgAAAAAAAAAAAD/2wBD" +

             "AAgGBgcGBQgHBwcJCQgKDBQNDAsLDB= kSEw8UHRofHh0aHBwgJC4nICIsIxwcKDcpLDAxNDQ0Hy" +

             "c5PTgyPC4zNDL/2wBDAQkJCQwLDBgN= DRgyIRwhMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjIy" +

             "MjIyMjIyMjIyMjIyMjIyMjIyMjIyMj= L/wAARCAB+AMcDASIAAhEBAxEB/8QAHwAAAQUBAQEBAQ" +

             "EAAAAAAAAAAAECAwQFBgcICQoL/8QA= tRAAAgEDAwIEAwUFBAQAAAF9AQIDAAQRBRIhMUEGE1Fh" +

             "ByJxFDKBkaEII0KxwRVS0fAkM2Jygg= kKFhcYGRolJicoKSo0NTY3ODk6Q0RFRkdISUpTVFVWV1" +

             "hZWmNkZWZnaGlqc3R1dnd4eXqDhIWG= h4iJipKTlJWWl5iZmqKjpKWmp6ipqrKztLW2t7i5usLD" +

             "xMXGx8jJytLT1NXW19jZ2uHi4+Tl5u= fo6erx8vP09fb3+Pn6/8QAHwEAAwEBAQEBAQEBAQAAAA" +

             "AAAAECAwQFBgcICQoL/8QAtREAAgEC= BAQDBAcFBAQAAQJ3AAECAxEEBSExBhJBUQdhcRMiMoEI" +

             "FEKRobHBCSMzUvAVYnLRChYkNOEl8R= cYGRomJygpKjU2Nzg5OkNERUZHSElKU1RVVldYWVpjZG" +

             "VmZ2hpanN0dXZ3eHl6goOEhYaHiImK= kpOUlZaXmJmaoqOkpaanqKmqsrO0tba3uLm6wsPExcbH" +

             "yMnK0tPU1dbX2Nna4uPk5ebn6Onq8v= P09fb3+Pn6/9oADAMBAAIRAxEAPwD3+iiigAooooAKKK" +

             "KACiiigAooooAKKKKACiiigAooooAK= KKKACiiigAooooAKKKKACiiigAqOeeO2t5biZtkUSF3Y" +

             "9lAyTT6z/EH/ACLeqf8AXnL/AOgGgF= uUx4w0MjP2qX/wFl/+Jo/4TDQ/+fqX/wABZf8A4muWjk" +

             "8u3QseAgyeuOM9qT7TGSMllz03Arkf= j/XFc3t32PSWATSdzqv+Ex0P/n6l/wDAWX/4mj/hMdD/" +

             "AOfqX/wFl/8Aia5rP+cmkyN3X+dSsT= 5F/wBnLudOPF+iEgC6lyen+jS//E1Z/t/T/wC9cf8AgL" +

             "L/APE1xx5K45w68+nzD/GvQl+7W9Of= OcWIoexlYzv7f0/+9cf+Asv/AMTR/b+n/wB64/8AAWX/" +

             "AOJrRoyM1oc5nf2/p/8AeuP/AAFl/w= DiadHrunyOiCSVS7BF328igknAGStX+veszWcCG1P/AE" +

             "+Qfn5goA1aKKKACiiigAooooAKKKKA= CiiigAooooAKKKKAErP8Qf8AIt6p/wBecv8A6Aa0O9Z+" +

             "v/8AIt6p/wBekv8A6AaXQFucE4DC2R= zhdh2k9A2Bg/WobbbAWtbuJUkERJkXpIAeT9elXURZLW" +

             "NSMqVBx74pFtYVbd5YJxj5jmuBux9B= yXSsUlOshFwbYj/aznFQ3t3qdlbtPKLbapA4z36VsEf5" +

             "zSFFfh0DDsDyKSlrsU6btuyvZyTS2k= Ulx5ZZmRgE/ulhXcl9S/fbY4mwf3eeOM/4Vx2BhQBgBl" +

             "HTHGRXoKgbRXVQd4s8vHL3kUXN+NzK= sePMAC+i45P1zSyy3oRhHEhcMPmJwCuf54q9jjFGOtbn" +

             "CUma/wDNTaI9vmENx/D2qjfm6MMQug= gH22Ax49PMFbh+tZesnMVqMZ/0yD/0MUAatFFFABRRRQ" +

             "AUUUUAFFFFABRRRQAUUUUAFFFFABUF= 7bLe2FxaMxVZ4mjLDqAwIz+tT0UAc2PCQCgDUp8AYHyL" +

             "0/Kl/wCEU/6iM3/ftP8ACujoqPZx7G= vt6nc5z/hE/wDqJTf9+0/wo/4RT/qJT/8AftP8K6LNLm" +

             "j2cew/rFX+Y53/AIRRSQTqE5wQfuL/= AIVr/Zbn/n+f/v2v+FW6M1SSWiM5zlN3kyp9muf+f5/+" +

             "/a/4UfZrn/n+f/v2v+FW6KZJU+y3X/= P+/wD37X/CoZdNkuDF594zrHKkoGwDlTmtGigAooooAK" +

             "KKKACiiigAooooAKKKKACiiigAoooo= AKKKKACiiigAooooAKKKKACkOaKX3oAiuJktoGlc4VRk" +

             "1zMWrX1/rUCRNsiznZjqueSfw/nTvE= F/51wLWN/3acyY7n0qTwvZkyT3r9ztjz2Hf+WPwrPnbl" +

             "ZHV7JRpc73OlopD1pa0OUKKKKACiii= gAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKA" +

             "CqmpXYsrGWY/eAwo9W7CrVYGsebqOq= QadCflX55G/u/5B/Wk9tCoK71KWi6e99dNcTZMSOST2d" +

             "u/4Zrq0RY1CooVR2FMtreO1t0hjGEQ= YFSmlGPKiqtRzlcO9FAoqjMKKKKACiiigAooooAKKKKA" +

             "CiiigAooooAKKKKACiiigAooooAKKK= KAENU9PtDAsk8nM9w2+Q+noPwHFXCKWgAooooAKKKKAC" +

             "iiigAooooAKKKKACiiigAooooAKKKK= ACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooA" +

            =    "KKKKACiiigAooooAKKKKACiiigD/2Q=3D=3D</css:data\>" +

            =    " <css:imageSize width=3D'200' height=3D'100'/>" +

            =    " <css:position x= =3D'0' y=3D'0'/></css:image\></css:Background\>" +

            =    " <css:Foreground&g= t;" +

            =    " <css:image encodeType=3D'base64'><css:data>/9j/4AAQSkZJRgABAQEAYABgAAD/2wBDAA= gGBgcGBQgHB" +

             "wcJCQgKDBQNDAsLDBkSEw8UHRofHh0= aHBwgJC4nICIsIxwcKDcpLDAxNDQ0Hyc5PTgyPC4zNDL" +

             "/2wBDAQkJCQwLDBgNDRgyIRwhMjIyM= jIyMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjIyM" +

             "jIyMjIyMjIyMjIyMjL/wAARCAABAAE= DASIAAhEBAxEB/8QAHwAAAQUBAQEBAQEAAAAAAAAAAAE" +

             "CAwQFBgcICQoL/8QAtRAAAgEDAwIEA= wUFBAQAAAF9AQIDAAQRBRIhMUEGE1FhByJxFDKBkaEII" +

             "0KxwRVS0fAkM2JyggkKFhcYGRolJic= oKSo0NTY3ODk6Q0RFRkdISUpTVFVWV1hZWmNkZWZnaGl" +

             "qc3R1dnd4eXqDhIWGh4iJipKTlJWWl= 5iZmqKjpKWmp6ipqrKztLW2t7i5usLDxMXGx8jJytLT1" +

             "NXW19jZ2uHi4+Tl5ufo6erx8vP09fb= 3+Pn6/8QAHwEAAwEBAQEBAQEBAQAAAAAAAAECAwQFBgc" +

             "ICQoL/8QAtREAAgECBAQDBAcFBAQAA= QJ3AAECAxEEBSExBhJBUQdhcRMiMoEIFEKRobHBCSMzU" +

             "vAVYnLRChYkNOEl8RcYGRomJygpKjU= 2Nzg5OkNERUZHSElKU1RVVldYWVpjZGVmZ2hpanN0dXZ" +

             "3eHl6goOEhYaHiImKkpOUlZaXmJmao= qOkpaanqKmqsrO0tba3uLm6wsPExcbHyMnK0tPU1dbX2" +

              "Nna4uPk5ebn6Onq8vP09fb3+Pn6/9= oADAMBAAIRAxEAPwD3+iiigD//2Q=3D=3D</css:data>" +

            =    " <css:imageSize wi= dth=3D'1' height=3D'1'/>" +

            =    " <css:position x= =3D'0' y=3D'0'/></css:image\>" +

            =    " <css:text\><css:properties color=3D'0 0 0' fontSize\=3D'10'/>" +

            =    " <css:position x= =3D'12' y=3D'12'/>" +

            =    " <css:SignatureInfos\>" +

            =    " <css:signatureInfo title=3D' ' id=3D'Subject'/>" +

            =    " <css:signatureInfo title=3D' ' id=3D'Date'/>" +

            =    " </css:SignatureInfos\></css:text\></css:Foreground<= /span>>" +

              " </css:Appearance\></css= :PdfSignatureInfo\>";

            =   

            =    //lectura del document PDF

            =    File file =3D new File("unsigned.pdf");

            =    FileInputStream fis =3D n= ew FileInputStream(file);

            =    byte\[\] pdfToSign =3D new b= yte\[(int)file.length()\];

            =    fis.read(pdfToSign);

            =    fis.close();

            =    byte\[\] signature =3D signPdf(pdfToSign, signatureInfo)= ;

            =    //guardem el PDF signat en un fitxer<= /o:p>

               java.io.FileOutputStream fos =3D new java.io.FileOutputStream("signed.pdf");

            =    if (fos!=3Dnull) {

            =           fos.write(signature);

            =           fos.close<= /span>();

               }

       }

}

  

\=  

Per construir la petició, invoquem els mètodes de la classe SmartSig= nRequest descrits a la taula següent:

Mètode

Paràmetres

setProfile

Constants.Profile.PDF per seleccionar el perfil de signatura PDF.=

setSignatureType

Format de la signatura: Constants.SignatureType.CMS

setPdfSignatureInfo

Tipus de signatura desi= tjat. En aquest exemple\= incloem informació de <= span class=3DSpellE>l’aparença de la signatura per tal que sigui visible.

setInputPdfBase64Data

Document PDF a signar codificat en Base64.

### 4.4.1=       = Paràmetres de signatura visible

Passarem a descriure els diferents paràmetres que permeten la configuració de la signatura visible en documents PDF.

#### 4.4.1.1  &nb= sp;      Element <css:PdfSignatureInfo\>

Aquest elem= ent conté informació sobre els= atributs de signatura propis d’A= dobe. L’estructura d’aquest element és la següent:\=

<xs:element name=3D"PdfSignatureInfo" type=3D&quo= t;css:PdfSignatureInfoType" m= axOccurs\=3D"unbounded"/>

<xs:complexType name=3D"PdfSignatureInfoType">

 <= ;xs:all\>

 <= ;xs:element name=3D"PdfAttributes" type=3D"css:PdfAttributesType"/>

 <= ;xs:element name=3D"Appearance" type=3D"css:Appeara= nceType" minOccurs=3D"0"/>

 <= ;/xs:all\>

 <= ;xs:attribute name=3D"= name" type=3D"xs:string" use=3D"optional"/>

 <= ;xs:attribute name=3D"order" type=3D"xs:integer" use=3D"optional"/>

</xs:complexType\>

On podem observat que l’element &l= t;css:PdfSignatureInfo\> inclou els següents elements:

o&nb= sp;  <css:PdfAttributes\>:  Configuració del mode de signatura.

o&nb= sp;  <css:Appearance\><= span lang=3DES style=3D'font-family:"Calibri",sans-serif;mso-bidi-font-family:Ar= ial'> \[Opcional\]. Paràmetres de \= l’aparença de la signatura. Si aquest element no està present, es= genera una signatura de tipus invisible.

**Element** **<c= ss:PdfAttributes\>**

L’element <css:PdfAttributes\> es <= span class=3DSpellE>pot fer servir en dos contexts bàsics:

o&nb= sp;  Confi= guració dels paràmetres relacionats amb el mode de signatura.

o&nb= sp;  Obten= ció d’informació sobre el mode de signatura en operacions de verificació.

La seva definició és la següent:

<xs:element name=3D"PdfAttributes" type=3D"<= span class=3DSpellE>css:PdfAttributesType"/>

<xs:complexType name=3D"PdfAttributesType">

       <xs:sequence\>\=

            = <xs:element name=3D"certified" minOccurs=3D"0">

            =         <xs:simpleType\>

            =               <xs:restriction base=3D&quo= t;xs:integer">

            =                      <xs:enumeration value=3D"0"/>

            =                      <xs:enumeration value=3D"1"/>

            =                      <xs:enumeration value=3D"2"/>

            =               </xs:restriction\>

            =         </xs:simpleType\>

            = </xs:element\> \=

            = <xs:element name=3D"signatureAlg">

            =         <xs:simpleType\>

            =               <xs:restriction base=3D&quo= t;xs:string">

            =                      <xs:enumeration value=3D"SHA1"/>

            =                      <xs:enumeration value=3D"DETACHED"/>

            =               </xs:restriction\>

            =         </xs:simpleType\>

            = </xs:element\> \=

            = <xs:element name=3D"validationMethod">

            =         <xs:simpleType\>

            =               <xs:restriction base=3D&quo= t;xs:string">

            =                      <xs:enumeration value=3D"PPKMS"/>

            =                      <xs:enumeration value=3D"PPKLITE"/>

            =               </xs:restriction\>

            =         </xs:simpleType\>

            = </xs:element\> \=

            = <xs:element name=3D"signaturePosition">

            =         <xs:simpleType\>

            =               <xs:restriction base=3D&quo= t;xs:string">

            =                      <xs:enumeration value=3D"FIRST"/>

            =                      <xs:enumeration value=3D"LAST"/>

            =                      <xs:enumeration value=3D"ADDLAST"/>

            =               </xs:restriction\>

            =         </xs:simpleType\>

            = </xs:element\> \=

            = <xs:element name=3D"pa= rams" minOccurs=3D"0">

            =         <xs:complexType\>

            =               <xs:sequence\>

            =                      <xs:element name=3D"location" type=3D"xs:string" minOccurs=3D"0"/>

            =                      <xs:element name=3D"re= ason" type=3D"xs:string" minOccurs=3D"0"/>

            =                      <xs:element name=3D"contactInfo" type=3D"x= s:string" minOccurs=3D"0"/>

            =               </xs:sequence\>

            =         </xs:complexType\>

            = </xs:element\> \=

       </xs:sequence\>

</xs:complexType\>

On es pot observar que l’element &l= t;css:PdfAttributes\> conté una seqüència dels següents elements, que veurem tot seguit:

o&nb= sp;  <css:signatureAlg\>

o&nb= sp;  <css:validationMethod\>

o&nb= sp;  <css:signaturePosition\><= /span>

o&nb= sp;  <css:params\> \[Opcional\]<= o:p>

\=  

**Element** **<c= ss:signatureAlg\>**

Indica el tipus de signatura PDF. La següent taula descriu els valors suportats per aquest element:

Valor

Tipus de sign= atura

SHA1

Signatura PKCS#7 attached sobre un resum criptogràfic SHA1= de les dades del PDF (adbe.pkcs7.sha1)

DETACHED

Signatura PKCS#7 detached sobre les d= ades d’un PDF (adbe.pkcs7.detached). Adobe recomana utilitzar= l’algorisme DETACHED per a un \= millor compliment dels <= span class=3DSpellE>estàndards.

**Element** **<c= ss:validationMethod\>**

Selecciona el plug\-= in amb el que validar la signatura PDF en AdobeReader. La següent taula descriu els valors suportats per aquest element:=

Valor

Tipus de sign= atura

PPKMS

Validador de Microsoft

PPKLITE

Validador d’Adobe\=

**Element** **<c= ss:signaturePosition\>**

Indica el posicionament de l’aparença de la signatura. La següent taula descriu els <= span class=3DSpellE>valors suportats per aquest element:

Valor

Tipus de sign= atura

FIRST

Validador de Microsoft

LAST

Validador d’Adobe\=

ADDLAST

Pàgina afegida expressament al= final del document.

**Element** **<c= ss:params\>**

Defineix les = propietats d’una signatur= a PDF (que corresponen a entrades del seu diccionari) mitjançant els següents elements:

o&nb= sp;  <css:location\>: Lloc de la signatura, indicat mitjançant una cadena de text. Correspon a l’entrada de = clau _Location_ del diccionari de la signatura.

o&nb= sp;  <css:reason\>: Compromís de signatura, indicat mitjançant una cadena de text. Corres= pon a l’entrada de clau\= _Reason_ del di= ccionari de signatura.

o&nb= sp;  <css:contactInfo\>\= : Informació de contacte del signa= tari (p.ex. el seu númer= o de telèfon), indicat mitjançant una cadena de text. Correspon a l’entrada de = clau _ContactInfo_ del diccionari de signatura.<= /p>

**Exemple** **d’element <<= span class=3DSpellE>css:PdfAttributes\>\=**

<css:PdfAttributes\>

       <css:validationMethod\>PP= KMS</css:validationMethod\>

       <css:signatureAlg\>SHA1&l= t;/css:signatureAlg\>

       <css:signaturePosition\>L= AST</css:signaturePosition\>

       <css:params\><= /span>

            = <css:location\>Barcelona&= lt;/css:location\>

            = <css:r= eason\>Razon de la firma</css:reason= \>

             <css:contactInfo\>+34 555 666 777</css:contactInfo\><= /span>

       </css:params\><= /span>

</css:PdfAttributes\>

\=  

**Element <css:Appearance<= /span>\>**

Defineix el <= span class=3DSpellE>format de l’aparença de l= a signatura. Si aquest element n= o està present, es genera u= na signatura invisible.

L’estructura d’aquest element és la següent:\=

<xs:element name=3D"Appearance" type=3D"css:Appeara= nceType" minOccurs=3D"0"/>

<xs:complexType name=3D"AppearanceType">

       <xs:sequence\>\=

            = <xs:element name=3D"Rect" type=3D"css:Rect= Type" minOccurs=3D"0"/>

            = <xs:element name=3D"Background" type=3D"css:Backgro= undType" minOccurs=3D"0"/>

            = <xs:element name=3D"Foreground" type=3D"css:Foregro= undType" minOccurs=3D"0"/>

       </xs:sequence\>\=

</xs:complexType\>

Conté els següents elements:

o&nb= sp;  <css:Rect\>: Espai on s’incrustarà l’aparença si és necessari crear un nou ca= mp de signatura. Si es treballa amb un camp de signatura buit, aquest<= /span> element no té cap efecte.

o&nb= sp;  <css:Background\><= span lang=3DES style=3D'font-family:"Calibri",sans-serif;mso-bidi-font-family:Ar= ial'>: Imatge de fons de l’aparença de la signatura.

o&nb= sp;  <css:Foreground\><= span lang=3DES style=3D'font-family:"Calibri",sans-serif;mso-bidi-font-family:Ar= ial'>: Imatge en primer pla de <= span class=3DSpellE>l’aparença de la signatura.

**Element** **<c= ss:Rect\>**

L’element <css:Rect\> indica on col·locar una signatura qu= an aquesta és visible.= La seva definició és la següent:\=

<xs:complexType name=3D"RectType">

       <xs:attribute name=3D"= x0" type=3D"xs:positiveInteger"/>\=

       <xs:attribute name=3D"= y0" type=3D"xs:positiveInteger"/>\=

       <xs:attribute name=3D"= x1" type=3D"xs:positiveInteger"/>\=

       <xs:attribute name=3D"= y1" type=3D"xs:positiveInteger"/>\=

</xs:complexType\>

Els atri= buts x0, y0, x1, i <= /span>y1 defineixen les coordenades del r= ectangle al que es mostra la signatura. Les coordenades = origen (0,0) es situen a la cantonada inferior esquerra de la pàgina.

o&nb= sp;  x0, y0: Punt inferior esq= uerre (expressat en píxels)

o&nb= sp;  x1, y1: Punt superior dre= t (expressat en píxels)

**Element** **<c= ss:Background\>**

L’element <css:Background\> defineix la imatge de fons (en segon pla) d’una signatura visi= ble. La seva definició és:

<xs:element name=3D"Background" type=3D"css:Backgro= undType"/>

<xs:complexType name=3D"BackgroundType">

       <xs:all\>

            = <xs:element name=3D"im= age" type=3D"css:ImageType"/>

       </xs:all\>

</xs:complexType\>

L’element\= <css:B= ackground\> només conté l’element <css:image\>, que descriurem més endavant.<= /span>

**Element** **<c= ss:Foreground\>**

L’element <css:Foreground\> defineix la imatge (en pr= imer pla) i el text de la sign= atura. La seva definició <= span class=3DSpellE>és:

<xs:element name=3D"Foreground" type=3D"css:Foregro= undType" minOccurs=3D"0"/>

<xs:complexType name=3D"ForegroundType">

       <xs:all\>

            = <xs:element name=3D"im= age" type=3D"css:ImageType"/>

            = <xs:element name=3D"te= xt" type=3D"css:TextType"/>\=

       </xs:all\>

</xs:complexType\>

L’element\= <css:F= oreground\> conté els dos elements següents:

o&nb= sp;  <css:image\>: Imatge de la signatura.

o&nb= sp;  <css:text\>: Text amb informació sobre la signatura.

**Element** **<c= ss:image\>**

L’element <css:image\> defi= neix la imatge d’una sig= natura. La seva definició <= span class=3DSpellE>és:

<xs:element name=3D"image" type=3D"css:ImageType"/>

<xs:complexType name=3D"ImageType">

       <xs:all\>

            = <xs:element name=3D"da= ta" type=3D"xs:string"/>

            = <xs:element name=3D"imageSize" minOccurs=3D"0">

            =         <xs:complexType\>

            =               <xs:attribute name=3D"width" type=3D"xs:positiveInteg= er"/>

            =               <xs:attribute name=3D"height" type=3D"xs:positiveInte= ger"/>

            =         </xs:complexType\>

            = </xs:element\><= /span>

            = <xs:element name=3D"position" type=3D"css:PositionT= ype" minOccurs=3D"0"/>

       </xs:all\>

       <xs:attribute name=3D"= encodeType">

            = <xs:simpleType\>

            =         <xs:restriction base=3D&quo= t;xs:string">

            =               <xs:enumeration value=3D&qu= ot;uri"/>

            =               <xs:enumeration value=3D"base64"/>

            =         </xs:restriction\>

            = </xs:simpleType\>

       </xs:attribute\>

</xs:complexType\>

L’element\= <css:i= mage\> conté els següents atributs:<= o:p>

\=  

o   <= /span>//image<= /span>/@encodeType: Indica la codificació utilitzada per l’element = <css:= data\> per definir la imatge de la signatura. La taula= següent defineix els valors suportats per aquest atribut:=

Valor d’encodeType <= /o:p>

Contingut de <= css:data\>

uri

Referència al fitxer de la imatge

base64

Imatge codificad= a en Base64

I els següents elements:

o&nb= sp;  <css:data\>: Imatge de la sign= atura codificada de la manera que indica l’atribut //image<= /span>/@encodeType. El format de la imatge ha de ser JPEG.

o&nb= sp;  <css:imageSize\>: Indica, mitjançant els següents atributs, el tamany de visualització d= e la imatge:

   =             \-    //imageSize/@width: Amplada de la imatge (en = píxels).

   =             \-    //imageSize/@height: Alçada de la imatge (en <= span class=3DSpellE>píxels).

Si aquest element s’omet, el tamany de visualització <= span class=3DSpellE>serà el real de la imatge\= .

o&nb= sp;  <css:Position\>: Indica la posició relativa de la imatge dins l’espai que defineix l’element <css:= Rect\>. En concret, aquest = element estableix la coor= denada inferior esquerra de la im= atge mitjançant els següents atributs:

   =             \-    //position/@x: Desplaçament horitzontal (en píxels).<= o:p>

   =             \-    //position/@y: Desplaçament vert= ical (en píxels).

**Element** **<css:text\>**

L’element <css:= text\> conté un text amb <= span class=3DSpellE>informació sobre la signatura. La definició és:

<xs:element name=3D"text" type=3D"css:TextType"/>

<xs:complexType name=3D"TextType">

       <xs:all\>

            = <xs:element name=3D"properties" minOccurs=3D"0">

            =         <xs:complexType\>

            =               <xs:attribute name=3D"= color" type=3D"xs:stri= ng"/>

            =               <xs:attribute name=3D"= fontSize" type=3D"xs:p= ositiveInteger"/>

            =         </xs:complexType\>

            = </xs:element\><= /span>

            = <xs:element name=3D"position" type=3D"css:PositionT= ype" minOccurs=3D"0"/>

            = <xs:element name=3D"SignatureInfos" type=3D"css:SignatureInfosType" minOccurs=3D"0"/>

       </xs:all\>

</xs:complexType\>

<xs:element name=3D"SignatureInfos" type=3D"= css:SignatureInfosType" minOccurs=3D"0"= ;/>

<xs:complexType name=3D"SignatureInfosType"><= /o:p>

       <xs:sequence\>\=

            = <xs:element name=3D"signatureInfo" maxOccurs=3D"unbounded">

            =         <xs:complexType\>

            =               <xs:attribute name=3D"title" type=3D"xs:string\= "/>

            =               <xs:attribute name=3D"= id">

            =                      <xs:simpleType\>

            =                            <xs:restriction base=3D&quo= t;xs:string">

            =                                   <xs:enumeration value=3D"Subject"/>

            =                                   <xs:enumeration value=3D"Issuer"/>

            =                                   <xs:enumeration value=3D&qu= ot;SerialNumber"/>

            =                                   <xs:enumeration value=3D"Reason"/>

            =                                   <xs:enumeration value=3D&qu= ot;Location"/>

            =                                   <xs:enumeration value=3D&qu= ot;ContactInfo"/>

            =                                   <xs:enumeration value=3D"Date"/>

            =                            </xs:restriction\>

            =                      </xs:simpleType\>

            =               </xs:attribute\>

            =         </xs:complexType\>

            = </xs:element\><= /span>

       </xs:sequence\>\=

</xs:complexType\>

L’element\= <css.text\> conté els següents elements:

o&nb= sp;  <css:properties\><= span lang=3DES style=3D'font-family:"Calibri",sans-serif;mso-bidi-font-family:Ar= ial'> \[Opcional\] Defineix, mitja= nçant els següents atributs, el color i el tamany del text:

   =             \-    //properties/@color: Color del text (en notació= RGB, amb valors ent= re 0 i 1).

   =             \-    //properties/@fontSize: Tamany de la font.

o&nb= sp;  <css:position\> \[Opcional\] Indica la posició relativa del text dins l’espai que defineix l’element <css:= Rect\>. En concret, aquest = element indica la coordenada inferior esquerra del text mitjançant\= els següents atributs:

   =             \-    //position/@x: Desplaçament horitzontal (en píxels).<= o:p>

   =             \-    //position/@y: Desplaçament vert= ical (en píxels).

o&nb= sp;  <css:SignatureInfos\> \[Opcional\]: Inclou una seq= üència d’elements <css:SignatureInfo\>\= , cadascun dels quals correspon a un camp textual que s’integra en el text de la signatura, i té els següents atributs:<= o:p>

   =             \-    //SignatureInfo/@title: Etiqueta que es mostra al \= costat del camp de text en= la                repres= entació gràfica de la signatura.

   =             \-    //SignatureInfo/@id: Identificador del camp de \= text. Aquest pot correspondre tant a camps                = del certificat (_Subject_, _Issuer_, _SerialNumber_), com a propietats de la signatura del PDF (_Reason_,               _Location_,= _ContactInfo_, _Date_) que est= an contingudes al seu = diccionari. Els valors que pot tenir són:

Camp

Descripció

Subject

Titular del certificat de la signatura

Issuer

Autoritat de certificació (CA) que ha emès<= /span> el certificat de la signatura

SerialNumber

Número de sèrie d= el certificat de la signatura

Reason

Raó de la generació de la signatura

Location

Lloc on s’ha portat a terme la signatura

ContactInfo

Dades de contacte de la persona/entitat que ha realitzat al signatura

Date

Data de la signatura

**Element** **<c= ss:StoreSignatureField\>**

Aquest elem= ent selecciona el camp de signatura al qual s’ha d’incrustar la signatura generada. La definició d’aquest element és\= la següent:

<xs:element name=3D"StoreSignatureField">\=

       <xs:complexType\>

            = <xs:attribute name=3D"= name" type=3D"xs:string" use=3D"required"/>

            = <xs:attribute name=3D"create" type=3D"xs:boolean" use=3D"required"/>

       </xs:complexType\>

</xs:element\>

L’element\= <css:S= toreSignatureField\> conté els següents atributs:<= o:p>

o&nb= sp;  //StoreSignatureField/@name: Identificador del camp de signatura.\=

o&nb= sp;  //StoreSignatureField/@create: Booleà que indica si cal crear el camp de signatura indicat per //StoreSignatureFi= eld/@name, si no existeix al PDF.

#### 4.4.1.2Plantilla de signatures PDF

Una plantilla de signatura PDF és un document XML que té la \= següent estructura:

<xs:element name=3D"PdfTemplate" type=3D"css:PdfTemplateType"/>

<xs:complexType name=3D"PdfTemplateType">

       <xs:sequence\>\=

            = <xs:element name=3D"PdfDocument" maxOccurs=3D"unbounded">

            =         <xs:complexType\>

            =               <xs:sequence\>\=

            =                      <xs:element name=3D"SignatureField" type=3D"css:PdfSignatureInfoType" maxOccurs\=3D"unbounded"/>

            =               </xs:sequence\>\=

            =               <xs:attribute name=3D"title" type=3D"xs:string\= " use=3D"optional"/>

            =         </xs:complexType\>

            = </xs:element\><= /span>

       </xs:sequence\>\=

</xs:complexType\>

<xs:complexType name=3D"PdfSignatureInfoType">

       <xs:all\>

            = <xs:element name=3D"PdfAttributes" type=3D"css:PdfAttributesType"/>

            = <xs:element name=3D"Appearance" type=3D"css:Appeara= nceType" minOccurs=3D"0"/>

       </xs:all\>

       <xs:attribute name=3D"= name" type=3D"xs:string" use=3D"optional"/>

       <xs:attribute name=3D"order" type=3D"xs:integer" use=3D"optional"/>

</xs:complexType\>

&l= t;css:PdfTemplate\>\= és l’element arrel de qualsevol plantilla de signatura PDF. Aquest element consisteix en una seqüència d’elements <css:PdfDocument\>\= , cadascun dels quals defineix una variació de la plantilla (és a dir, plantilles diferents en la pràctica). D’aquesta manera, quan s’hagi de signar un document PDF, fent ús d’una plantilla determinada, s’utilitzarà la “variant” que contingui l’element /css:PdfTemplate/css:PdfDocument, l’a= tribut /css:PdfTemplate/css:PdfDocument/@title del = qual coincideixi amb el títol del document PDF. És a dir, amb el valor que estigui associat a la clau Title del diccionari d’informació d= el document. Cal tenir en compte que sempre hi hauran correspondències (= matching) entre un document PDF i un element /css:PdfTemplate/css:PdfDocument que \= manqui de l’atribut title.=

Per un altre costat, en aquells casos = en que:

o&nb= sp;  El títol del document PDF no coincideixi amb l'atribut title de cap dels elements /css:PdfTemplate /css:Pdf= Document de la plantilla.

o&nb= sp;  I, a més, no hi hagi cap element /css:PdfTemplate /css:PdfDo= cument que no tingui l'atribut title.

Aleshores, s'haurà d'utilitzar la pl= antilla de signatures PDF per defe= cte, és a dir, la planti= lla urn:Safelayer:TWS:policies:common:template= s:pdf:default. Aquesta plantilla es descriu més endavant en Plantilla= de signatures PDF per defecte.

o&nb= sp;  Cada element <css:PdfDocument\> cont= é un nombre il·limitat d'elemen= ts <css:SignatureField\>, cadascun dels quals descriu els atributs i l'aparença d'un camp de signatura del docum= ent PDF.

o   Cada element &l= t;css:SignatureField\> conté els següents elements:

               \-    <css:PdfAttribut= es\>, Que determina les característiques de la signatura. Ve= gi Element        =         <css:PdfAttributes\> per = obtenir més detalls sobre aquest element.

   =             \-   <css:Appearance<= /span>\>, Que determina l'aparença "visual" de = la signatura. Vegi Element          =       &l= t;css:Appearance\><= span lang=3DEN-GB style=3D'font-family:"Calibri",sans-serif;mso-bidi-font-family= :Arial; mso-ansi-language:EN-GB'> per a més detalls sobre aquest element. Si aquest element s'omet, la signat= ura              que es g= eneri serà invisible.

o&nb= sp;  I els següents atributs:

   =             \-    //SignatureField/@name, que identifica (pel seu nom) el camp de signatura= del document            <= /span>PDF a què es refereixen\= els atributs i l'aparença que defineix <= span class=3DSpellE>aquest element.

   =             \-    //SignatureField/@order, que identifica (pel seu\= nombre d'ordre) el camp de signa= tura del        document= PDF a què es refereixen els atributs i l'aparença que defineix <= span class=3DSpellE>aquest element, tenint en            = compte que el valor 0 identifica el "següent" camp de signatura (sigui quin sigui el seu número           = d'ordre).

L'element /css:PdfTemplate/css:PdfDoc= ument/css:SignatureField que \= s'utilitzarà per establir els atributs<= /span> i l'aparença de la signatura PDF es determinarà de la manera següent:

a) Si en la petició\= s'ha especificat el nom del camp de signatura= (element //DSS:OptionalInputs/css:StoreSignatureField) aleshores s'utilitzarà l'element /css:PdfTemplate/css:PdfDocument<= /span>/css:SignatureField l'at= ribut //SignatureField/@name del qual contingui = el mateix valor.

b) Si l'atribut //Signat= ureField/@name no és present, la petició no conté l'element //DSS:OptionalInputs/css:Sto= reSignatureField, o bé no hi ha coincidència entre un i altre, llavors<= /span> s'ha d'utilitzar l'element /css:PdfTemplate/css:PdfDocument<= /span>/css:SignatureField l'at= ribut //SignatureField/@order del qual sigui 0 o = coincideixi amb el resultat d'incrementar (e= n un) el nombre de camps de signatura que contingui el document PDF.

c) Si no s'ha pogut seleccionar cap element /css:PdfTemplate/css:PdfDocument/css:SignatureFie= ld en base als criteris <= span class=3DSpellE>anteriors, llavors cal utilitzar el (únic) camp = /css:Pdf= Template/css:PdfDocument/css:SignatureFie= ld de la plantilla per defecte del sistema (és a dir, la plantilla urn:Safe= layer:TWS:policies:common:templates:pdf:default). Aquesta plantilla es descriu seguidament.

**Plant= illa de signatures PDF per defe= cte**

TrustedX cont= é una plantilla per defecte per \= realitzar signatures PDF, que s'iden= tifica per urn:Safelayer:TWS:policies:common:templates:pdf:default i que té la següent definici= ó:

<css:PdfTemplate xmlns:css\=3D"http://www.safelayer.com/TWS&= quot;>

       <css:PdfDocument\>

            = <css:SignatureField\>

            =         <css:PdfAttributes\>\=

            =               <css:signatureAlg\>DETACH= ED</css:signatureAlg\>

            =               <css:validationMethod\>PP= KMS</css:validationMethod\>

            =                <css:signaturePosition\>LAST</css:signaturePosition\>

            =         </css:PdfAttributes\>\=

            = </css:SignatureField\>

       </css:PdfDocument\>

</css:PdfTemplate\>

On es p= ot observar que, quan es genera una signatura en u= n document PDF, utilitzant = la plantilla per defecte de T= rustedX, aquesta signatura tindrà les següents característiques:

o&nb= sp;  Serà<= /span> invisible i s'ubicarà a l'= última pàgina.

o&nb= sp;  El seu format serà el d'una signatura PKCS#7 de tipus<= /span> detached. És a dir, s'ha d'associar el valor adbe.pkcs.detached= a la clau _SubFilter_ del diccionari de = la signatura.

o&nb= sp;  El signature-handler que, de manera preferent, s'ha<= /span> d'utilitzar per a verificar la signatura és el de Microsoft. És a = dir, s'ha d'associar el valor Adobe.PPKMS a la \= clau Filter del diccionari de la signatura.

**Exemple** **de plantilla de signature= s PDF**

El següent codi XML és un exemple de plantilla de signatur= es PDF:

<?xml version=3D"1.0" encoding=3D"UTF-8"?>

<css:PdfTemplate xmlns:css\=3D"http://www.safelayer.com/TWS&= quot; xmlns:xsi\=3D"http://www.w3.org/2001/XMLSchema-in= stance">

       <css:PdfDocument title=3D"Document1">

            = <css:SignatureField name=3D"Signature1">

            =         <css:PdfAttributes\>\=

            =               <css:signatureAlg\>SHA1&l= t;/css:signatureAlg\>

            =               <css:validationMethod\>PP= KMS</css:validationMethod\>

            =                <css:signaturePosition\>ADDLAST</css:signaturePosition\>

            =               <css:params\><= /span>

            =                      <css:location\>Barcelona&= lt;/css:location\>

            =                      <css:reason\>Author</<= span class=3DSpellE>css:reason\>

            =                      <css:contactInfo\>+345818090</css:contactInfo\>

            =               </css:params\><= /span>

            =         </css:PdfAttributes\>\=

            = </css:SignatureField\>

            = <css:SignatureField order=3D"0">

            =         <css:PdfAttributes\>\=

            =               <css:signatureAlg\>SHA1&l= t;/css:signatureAlg\>

            =               <css:validationMethod\>PP= KMS</css:validationMethod\>

            =                <css:signaturePosition\>ADDLAST</css:signaturePosition\>

            =               <css:params\><= /span>

            =                      <css:location\>Barcelona&= lt;/css:location\>

            =                      <css:reason\>Author</<= span class=3DSpellE>css:reason\>

            =                      <css:contactInfo\>+345818090</css:contactInfo\>

            =               </css:params\><= /span>

            =         </css:PdfAttributes\>\=

            =         <css:Appearance\>

            =               <css:Rect x0=3D"31&quo= t; y0=3D"200" x1=3D"557" y1=3D"40"/>

            =               <css:Background\>

            =                      <css:image encodeType\=3D"base64">

            =                            <css:data\>/9j/4...Q=3D=3D</\= css:data\>

            =                            <css:imageSize width=3D"400" height=3D"40"/>

            =                            <css:position x=3D"50&= quot; y=3D"35"/>

            =                      </css:image\>

            =               </css:Background\>

            =               <css:Foreground\>

            =                      <css:image encodeType\=3D"base64">

            =                            <css:data\>/9j/...ZCg\=3D= =3D</css:data\>

            =                            <css:imageSize width=3D&quo= t;80" height=3D"30"/>

            =                            <css:position x=3D"223= " y=3D"1"/>

            =                      </css:image\>

            =                      <css:text\>

            =                            <css:properties color\=3D"0 0 0" fontSize\=3D"5"/>

            =                            <css:p= osition x=3D"150" y=3D"35"/>

                                       = <css:SignatureInfos\>

                                       =        <css:signatureInfo title\=3D"Autor de la firma: " id=3D"Subject"/>

                                       =        <css:signatureInfo title\=3D"Emisor del certificado: " id=3D&qu= ot;Issuer"/>

                                       =        <css:signatureInfo title\=3D"Número de serie: " id=3D"SerialNumber"/>

                                       =        <css:signatureInfo title\=3D"Razón: " id=3D"Reason"/&= gt;

                                       =        <<= span class=3DGramE>css:signatureInfo title=3D"Localitzación: " id=3D"Location"/>

            =                                   <css:s= ignatureInfo title\=3D"Información de contacto: " i= d=3D"ContactInfo"/>

                                       =        <css:signatureInfo title\=3D"Fecha de firma: " id=3D"Date&= quot;/>

                                       = </\= css:SignatureInfos\>

            =                      </css:text\>

            =               </css:Foreground\>

            =         </css:Appearance\>

            = </css:SignatureField\>

       </css:PdfDocument\>

       <css:PdfDocument\>

            = <css:SignatureField order=3D"0">

            =         <css:PdfAttributes\>\=

            =               <css:signatureAlg\>SHA1&l= t;/css:signatureAlg\>

            =               <css:validationMethod\>PP= KMS</css:validationMethod\>

            =                <css:signaturePosition\>LAST</css:signaturePosition\>

            =         </css:PdfAttributes\>\=

            = </css:SignatureField\>

       </css:PdfDocument\>

</css:PdfTemplate\>

5      = Gestió de dades de volum gran

Si els documents XML inclouen elements amb valors de volum gran, Axis experimenta problemes de rendiment. Per pal·liar= aquests problemes, podem guardar en arxiu aquests valors, deixant a l’XML una referència a aquest arxiu. D’aquesta manera, = el tamany de l’XML que gesti= ona Axis es redueix considerablemen= t. Més endavant, en la= capa de transport, es substitueixe= n les referències per les dades guardades en arxiu.

Per defecte, les da= des no es tracten com a arxiu.

5.1      Gestió de peticions amb dades de gran tamany
-----------------------------------------------------

Quan el d= ocument a signar tingui un volum considerable, i cal enviar-lo sencer en la petició de signatura, podem experimentar problemes de \= rendiment d’Axis.

La classe SmartSig= nRequest ofereix certs mètodes que permeten gestionar com= a arxius les dades de gran volum.

Mètodes:

o   setInputBase64Data(fileName, format): = Per documents binaris.

o   setInputXmlBase64(fileName, format): Per documents XML.

o   setInputPdfBase64Data(<= span class=3DSpellE>fileName, format): = Per documents PDF.

On:

fileName és el nom del fitxer que conté les dades a signar

format és el format de les guard= ades en arxiu, i que pot prendre els següents valors:

   =             \-    Constants.SourceFormat.BASE64

               \-    Constants.Sourc= eFormat.RAW

La classe SmartSig= nRequest també ofereix certs\= mètodes que permeten que = en la resposta les dades de gran volum= puguin tractar-se també com a arxius:

o   enableSignatureBase64(format): Per signatures binàries.

o   enableSignatureXmlBase64(format): Per signatures XML.

o   enableDocumentW= ithSignaturePdf(f= ormat): Per documents PDF signats.

o   enableDocumentWithSignatureXmlBase64(format): Per signatures XML enveloped.<= /p>

On:

format és el format de les guard= ades en arxiu, i que pot prendre els següents valors:

   =             \-    Constants.SourceFormat.BASE64

               \-    Constants.Sourc= eFormat.RAW

Els següents mètodes deshabilitarien l’habilitat amb els corresponents mètodes anteriors:

o   disableSignatureBase64(format): Per signatures binàries.

o   disableSignatureXmlBase64(format): Per signatures XML.

o   disableDocument= WithSignaturePdf(f= ormat): Per documents PDF signats.

o   disableDocumentWithSignatureXmlBase64(format): Per signatures XML enveloped.<= /p>

En fer un _disable_ <= span class=3DSpellE>després d’un _enable_, deshabilitarem el tractament com a= arxiu de les dades corresponents= . Recordem que per defecte el tractament com a arxiu està deshabilitat.

**NOTA 1**: En cas de que habilitem la gestió de da= des de la resposta en fitxer, aquests es guardaran al director= i indicat al paràmetre Response= .savePath de la configuració de l’Smart= Wrapper. Si aquest paràmetre\= no és present, els arxius es guardaran al dir= ectori d’execució.

**NOTA 2**: Si volem que les = dades d’entrada s’agafin directament d’un directori base concret, c= al indicar el paràmetre Request.loadPath a la configuració d’SmartWra= pper. Si no s’especifica, el dir= ectori base serà el d’execució.

5.2      Gestió de respostes amb dades de gran tamany
-----------------------------------------------------

Si s’ha habilitat en la petició de signatura el tractament co= m a fitxers de dades de la r= esposta, en cas de voler rec= uperar aquestes dades per codi, = haurem de fer-ho mitjançant els mètodes que veurem a continuació.

La classe SmartSig= nResponse ofereix doncs mètodes que permeten obtenir les dades de la resposta quan<= /span> aquestes s’han gestionat com a arxius. En aquest cas es = tractarà de signatures o = documents signats.

Mètodes:

o&nb= sp;  getDocumentWithSignaturePdf(<= /span>): Per= obtenir la referència a u= n document PDF signat.\=

o&nb= sp;  getDocumentWithSignatureXml(<= /span>):  Per obtenir\= la referència a un document = que conté la referència a una signatura XML enveloped.

o&nb= sp;  getSignatureBase64(): Per obtenir la referència<= /span> a una signatura binària.

o&nb= sp;  getSignatureXml\= (<= /span>): Per= obtenir la referència a u= na signatura XML.

Quan parl= em de referència volem\= dir el nom del fitxer al directori de sortida.

A partir de els referències obtingudes amb els mètodes anteriors, podem re= cuperar per codi el contingut dels fitxers que contenen les dades de la respost= a:

o   ge= tReferenceFileContent(String reference, boolean deleteFile)

On:

o&nb= sp;  reference és el nom del fitxer.

o&nb= sp;  deleteFile és un booleà amb el qual podem esborrar el document guardat en fitxer:

   =             \-   true: L’arxiu que conté= el valor, s’esborrarà després= de llegir el seu contingut

   =             \-   false: L’arxiu no s’esborrarà.

  

\=  

5.3      E= xemple de gestió en arxius per generació d’una signatura XAdES\-BES= enveloping
-------------------------------------------------------------------------------------------

import org.apache\= .axis.encoding.Base64;

import org.apache.axis.message.SOAPHeaderElement;

import org.apache.commons.configuration.Configuration;

import utils.\*; <= o:p>

import com.safelayer.trustedx.client.smartwrapper.\*;

public class CreateSign= ature\_XAdES\_BES\_Enveloped\_BigFile {

       private static final String path\_in =3D "in/docs\_to\_sign/BigFiles/";

       private static final String path\_out =3D "out/Sign= atures/BigFiles/";

       private static final String filename =3D "Demo-BigFile.xml\= ";

       public static void main(String\[\] a= rgs) {

            = try {

            =         Configuration conf =3D TrustedXConfiguration.getConfiguration\= ();

            =         String host =3D conf.getString("host");

            =         String distinguishedName =3D conf.getString("disti= nguishedname");

            =         String dipositari =3D conf.getString("dipositari");

            =         String rol =3D conf.getString("rol");

            =         // Definition of Signature Request endpoint

            =         SmartSignRequest ssr =3D = new SmartSignRequest(host);

            =         // Add customized header elements for SOAP

            =         Stub stub =3D (Stub) ssr.getStub();

            =         stub.setHeader(null, "= ;Rol", rol);

            =         stub.setHeader(null, "= ;Dipositari", dipositari);

            =         // XML Signature (XAdES)

            =         ssr.setProfile(Constants.Profile.XADES);

            =         // Referència al fitxer que conté les dades a signar

                    // Paràmetres: path (codificat en Base64) del fitxer<= /span> + tipus de dades del fitxer<= /span> (Raw o Base64)

                    ssr.setInputXm= lBase64File(Base64.encode((path\_in + filename).getBytes()), Constants.SourceFormat.RAW);

            =         // Habilitem la gestió en arxiu de la sig= natura en la resposta

                 ssr.enableDocumentWithSignatureXmlBase64File(Constants.SourceFormat.RAW);

            =         // XAdES signature form

            =         ssr.setSignatureFormat(Constants.SignatureFormat.BES);

            =         // Signature Placement

            =        ssr.setSignatur= ePlacement(Constants.SignaturePlacement.ENVELOPED);

            =         ssr.setXmlEnvelopedXPathAfter("//\*\[local-name()= =3D'ssc'\]//\*\[local-name()=3D'description'\]");

            =         // Key selection using Distinguished Name

            =         ssr.setKeySubjectName(distinguishedName);

            =         // Sending request

            =         SmartSignResponse ssrs = =3D ssr.send();

            =         // Retrieveing signature

            =         if (UtilTrustedX.checkSW(ssrs.getResultMajor(), ssr= s.getResultMinor(), ssrs.getResultMessage())) { <= /p>

            =               String destFilename =3D path\_out<= /span> + filename.substring(0, filename.lastIndexOf("."))

            =               \+ "\_Signature\_XAdES\_BES\_Enveloped.xml"; =

            =               Util.writeBinaryFile(destFilenam= e, ssrs.getDocumentWithSignatureXml().getBytes());

            =         }

            = } catch (Exception e) {

            =         e.printStackTrace(); \=

            = }

       }

}

6      = E= xemple \= d’ús amb SoapUI
=====================================

A l’apartat de Documentació de Integració d’aquest servei es disposa d’uns exemples de SOAPUI amb un certifica= t en format pkcs#12 (pin : 1234) per realitzar l’aute= nticació al servei.

SoapUI és una eina per a realitzar proves d’APIs del tipus SOAP o REST. Es pot\= descarregar gratuïtament = a la web [https://www.soapui.org/](3D"https://www.soapui.org/"). Aquest breu guía ha sigut creada amb la versió SoapUI 5.3.0.

6.1      Importar un projecte
-----------------------------

Obrir Soap= UI i utilitzar l’opció\= _Import_ si= tuada al menú de la part superior.

Seleccionar el projecte proporcionat a la web. L’eina crearà una estructura semblant a la seguent:

Els missatges SOAP disponibles són:

·        Signatura amb ROL i= autenticació amb certificat

·      =   Signatura sense ROL i <= span class=3DSpellE>amb autenticació amb certificat\=

6.2      A= fegir \= certificat PKCS#12
---------------------------------------

Per utilitzar un certificat personal per autent= icar amb el servei de signatura, prémer el botó _Preferences_ situat al menú superior de l’eina.

A l’apartat _SSL Setting_ seleccionar el certificate PKCS#12 proporcionat i posar la contrasenya tal com s’indica a la següent figura:

