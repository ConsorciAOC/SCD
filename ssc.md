![Shape2](RackMultipart20220630-1-6kytqz_html_6f1bdbd5e15159df.gif) ![Shape3](RackMultipart20220630-1-6kytqz_html_c8bac1e78d20a1be.gif) ![Shape1](RackMultipart20220630-1-6kytqz_html_34b9f772e3098a80.gif)

# **DI - Signador Centralitzat (SSC)**

![](RackMultipart20220630-1-6kytqz_html_f82d96c26cc03594.png)

![Shape5](RackMultipart20220630-1-6kytqz_html_7cc993dc0b22ceb9.gif) ![](RackMultipart20220630-1-6kytqz_html_e7cf959e7fe4dc1d.png)

Realitzat per: Consorci AOC – Servei Eines de Signatura

Versió: 1.3.3

Fecha: 6/30/22

**Control del document**

**Informació general**

| **Título:** | RackMultipart20220630-1-6kytqz.docx |
| --- | --- |
| **Creat per:** | Consorci AOC – Servei Eines de Signatura |
| **Nom del documento:** | RackMultipart20220630-1-6kytqz.docx |

**Histórico de revisiones**

| **Versió** | **Data** | **Autor** | **Comentaris** |
| --- | --- | --- | --- |
| 1.3.2 | 26/10/2016 | Servei Eiunes de Signatura | Actualització de contingut. |
|
 |
 |
 |
 |

Index

[1Introducció 4](#_Toc483913121)

[2URLS de l&#39;SSC 5](#_Toc483913122)

[2.1PREPRODUCCIÓ 5](#_Toc483913123)

[2.2PRODUCCIÓ 5](#_Toc483913124)

[2.3Connexió 5](#_Toc483913125)

[2.3.1Habilitar la propietat de JVM 6](#_Toc483913126)

[2.3.2Habilitar la propietat com a variable d&#39;entorn 6](#_Toc483913127)

[3SmartWrapper 7](#_Toc483913128)

[3.1L&#39;API SmartWrapper 7](#_Toc483913129)

[3.2Accés a l&#39;SSC mitjançant SmartWrapper 7](#_Toc483913130)

[3.3Classes de l&#39;API SmartWrapper 8](#_Toc483913131)

[3.3.1Classe per gestionar peticions SmartWrapper de signatura 8](#_Toc483913132)

[3.3.2Classe per gestionar respostes SmartWrapper de signatura 8](#_Toc483913133)

[3.3.3Classe SmartHeader per gestionar la capçalera 8](#_Toc483913134)

[3.3.4Classe Constants per gestionar constants 8](#_Toc483913135)

[3.4Configuració d&#39;SmartWrapper 9](#_Toc483913136)

[3.4.1JDK 9](#_Toc483913137)

[3.4.2Llibreries del client 9](#_Toc483913138)

[3.5Arxiu smartwrapper.properties 9](#_Toc483913139)

[4Serveis de Signatura 11](#_Toc483913140)

[4.1Signatura CMS attached 11](#_Toc483913141)

[4.2Signatura XML enveloped 13](#_Toc483913142)

[4.3Signatura XAdES-T detached a partir del hash d&#39;un document 15](#_Toc483913143)

[4.4Signatura de documents PDF 16](#_Toc483913144)

[4.4.1Paràmetres de signatura visible 19](#_Toc483913145)

[5Gestió de dades de volum gran 29](#_Toc483913146)

[5.1Gestió de peticions amb dades de gran tamany 29](#_Toc483913147)

[5.2Gestió de respostes amb dades de gran tamany 30](#_Toc483913148)

[5.3Exemple de gestió en arxius per generació d&#39;una signatura XAdES-BES enveloping 31](#_Toc483913149)

[6Exemple d&#39;ús amb SoapUI 32](#_Toc483913150)

[6.1Importar un projecte 32](#_Toc483913151)

[6.2Afegir certificat PKCS#12 32](#_Toc483913152)

# 1Introducció

El Signador Centralitzat és la solució que dóna cobertura al concepte de sistema de signatura electrònica per a l&#39;actuació administrativa automatitzada, tal com es descriu a la LAECSP (art.18, Llei 11/2007). Permet la custòdia i ús posterior de segells electrònics de les administracions públiques, òrgans o entitats de dret públic de Catalunya que ho sol·licitin, agilitzant la posada en marxa d&#39;un sistema automatitzat de signatura electrònica de documents des d&#39;un dispositiu remot. En aquesta URL es pot consultar la informació del servei : [https://www.aoc.cat/serveis-aoc/signador-centralitzat/](https://www.aoc.cat/serveis-aoc/signador-centralitzat/)

Les claus associades al segell electrònic, resideixen en magatzems de claus protegits per un dispositiu criptogràfic segur (HSM). El dispositiu està certificat sota els criteris de Common Critera EAL4+, oferint les màximes garanties en matèria de seguretat i custòdia de claus.

La guia bàsica d&#39;integració al Servei de Signatura Centralitzada (SSC) és un document que va dirigit a desenvolupadors que vulguin integrar les seves aplicacions de gestió amb l&#39;SSC de l&#39;AOC.

El lector d&#39;aquest document ha de ser un professional amb coneixements en programació avançada en el llenguatge Java. És molt recomanable disposar també de coneixement sobre Webservices, missatgeria SOAP, WS-Security, ús de certificats i signatures digitals.

L&#39;objectiu d&#39;aquest document és oferir una guia bàsica d&#39;integració amb l&#39;SSC mitjançant tecnologia Java

La disposició de capitols és la següent:

Al capítol 2 s&#39;indiquen les URLs d&#39;accés als Webservices de signatura de l&#39;SSC. Al capítol 3 es descriu l&#39;SmartWrapper, API d&#39;integració a l&#39;SSC. Al capítol 4 es descriu com accedir als serveis de creació de signatura mitjançant SmartWrapper, amb codi d&#39;exemple. També s&#39;indica com parametritzar la signatura visible de documents PDF. Finalment, al capítol 5 es descriu la gestió de dades de gran volum amb l&#39;API SmartWrapper

L&#39;accés al servei es fa mitjançant canal segur SSL amb autenticació de client. Les següent són les URLs per accedir al Servei de Signatura Centralitzada pels entorns de PREPRODUCCIÓ i PRODUCCIÓ.

# 2URLS de l&#39;SSC

L&#39;accés al servei es fa mitjançant canal segur SSL amb autenticació de client. Les següent són les URLs per accedir al Servei de Signatura Centralitzada pels entorns de PREPRODUCCIÓ i PRODUCCIÓ.

## 2.1PREPRODUCCIÓ

La URL d&#39;accés al Webservice de signatura de l&#39;SSC a l&#39;entorn de PREPRODUCCIÓ mitjançant certificat és:

[https://ssc.preproduccio.catcert.cat:8443/trustedx-sgw/SignCert](https://ssc.preproduccio.catcert.cat:8443/trustedx-sgw/SignCert)

## 2.2PRODUCCIÓ

La URL d&#39;accés al Webservice de signatura de l&#39;SSC a l&#39;entorn de PRODUCCIÓ mitjançant certificat és:

[https://ssc.catcert.cat:8443/trustedx-sgw/SignCert](https://ssc.catcert.cat:8443/trustedx-sgw/SignCert)

## 2.3Connexió

Els protocols utilitzats per realitzar les connexions SSL depenen de la versió de Java amb la qual s&#39;executa l&#39;aplicació. Per defect SmartWrapper utilitza protocols segurs per xifrar la comunicació amb el servidor utilitzant TLS amb la versió 1.1 o 1.2. D&#39;altra banda, les versions de TLS per defecte que s&#39;utilitzen en cada versió de Java varien, tal com mostra la següent taula:

![](RackMultipart20220630-1-6kytqz_html_eba657a890c2c4cb.png)

Per tal motiu, per a versions anteriors de Java 1.7.XX cal habilitar l&#39;ús de TLSv1.0 per a realitzar les comunicacions SSL. Hi ha dues formes d&#39;habilitar aquest protocol, mitjançant una variable global al sistema o amb una variable a la màquina virtual de Java (JVM).

### 2.3.1Habilitar la propietat de JVM

Abans de fer la connexió amb TrustedX (mètode send) cal introduir el següent codi:

System.setProperty(&quot;PropertyAllowTls10AsClient&quot;, &quot;true&quot;);

Aquesta propietat habilitarà l&#39;ús de TLSv1.0 a la màquina virtual de Java per a l&#39;aplicació de SmartWrapper.

### 2.3.2Habilitar la propietat com a variable d&#39;entorn

Depenent del sistema operatiu, la configuració de variables d&#39;entorn difereix. Cal afegir la variable d&#39;entorn PropertyAllowTls10AsClient amb valor true.

## 2.4

# 3SmartWrapper

En aquest capítol oferim una versió general de l&#39;API SmartWrapper proporcionada per accedir a l&#39;SSC.

## 3.1L&#39;API SmartWrapper

SmartWrapper és una API desenvolupada sobre Axis per crear aplicacions client sense necessitat d&#39;aprofundir en la complexitat d&#39;Axis (permet també l&#39;accés a estructures Axis d&#39;ús avançat). SmartWrapper permet generar aplicacions Java senzilles, i amb poques línies de codi.

![](RackMultipart20220630-1-6kytqz_html_6fd5d0ba8d10d6d4.gif)

## 3.2Accés a l&#39;SSC mitjançant SmartWrapper

A continuació resumim els passos necessaris per enviar una petició a l&#39;SSC, obtenir la resposta i consultar si s&#39;ha processat correctament.

Per invocar el servei i avaluar la resposta:

1. Creem una instància de la classe SmartSignRequest corresponent al servei invocat.
2. Recuperem l&#39;objecte Stub de la classe Axis mitjançant el mètode getStub.
3. Utilitzem el mètode setHeader per a l&#39;objecte Stub afegint els tags (Rol i Dispositari).
4. Creem una instància de la classe Request corresponent al servei invocat.
5. Realitzem les operacions set necessàries per construir una petició vàlida.

**Important** : A la petició hem de definir tant el perfil escollit (mitjançant el mètode setProfile) com els paràmetres adequats a aquell perfil.

1. Enviem la petició (mitjançant la operació send) per obtenir un objecte del tipus Response.
2. Consultem, mitjançant els mètodes de l&#39;objecte Response, el resultat de la petició. Si la petició ha sigut processada correctament, obtenim el valor dels paràmetres retornats amb les mètodes get del mateix objecte Response.

## 3.3Classes de l&#39;API SmartWrapper

En aquest punt descrivim les classes utilitzades per l&#39;API SmartWrapper.

### 3.3.1Classe per gestionar peticions SmartWrapper de signatura

La classe de l&#39;API SmartWrapper que serveix per gestionar peticions de signatura, és la següent:

- Serveis de signatura digital: SmartSignRequest

Aquest classe inclou els següents mètodes:

- Mètode send per enviar la petició. Aquest mètode retorna un objecte de la classe associada amb la resposta corresponent.

- Mètodes per assignar valors als paràmetres necessaris en cada petició. Els noms d&#39;aquests mètodes segueixen la sintaxi set\&lt;Param\&gt;, on \&lt;Param\&gt; és el nom del paràmetre al que assignen valor (amb la primera lletra en majúscules).

### 3.3.2Classe per gestionar respostes SmartWrapper de signatura

La classe de l&#39;API SmartWrapper per gestionar respostes de signatura, és la següent:

- Serveis de signatura digital: SmartSignResponse

Aquesta classe inclou mètodes per consultar els paràmetres de la resposta. Els noms d&#39;aquests mètodes segueixen la sintaxi get\&lt;Param\&gt;, on \&lt;Param\&gt; és el nom del paràmetre el valor del qual es vol consultar (amb la primera lletra en majúscules).

### 3.3.3Classe SmartHeader per gestionar la capçalera

La classe SmartHeader gestiona la capçalera de les peticions i inclou informació per la correcta autenticació al servei. En concret, suporta autenticació amb certificat.

Tanmateix, l&#39;autenticació la portarem a terme sempre mitjançant certificat digital per l&#39;aplicació en concret que vol consumir els serveis de l&#39;SSC.

Cal emfatitzar que el servei inclou dos paràmetres nous a la capçalera: _Rol_ i _Dispositari_. Ambdós elements son presents al fitxer de propietats.

### 3.3.4Classe Constants per gestionar constants

La classe Constants defineix una sèrie de constants per facilitar l&#39;ús de l&#39;API i reduir el risc d&#39;error tipogràfics.

## 3.4Configuració d&#39;SmartWrapper

### 3.4.1JDK

El sistema on s&#39;executin ha de tenir instal•lada la **Java JDK1.4 (o superior).**

### 3.4.2Llibreries del client

Les llibreries necessàries pel correcte funcionament del client basat en SmartWrapper són:

- smartwrapper.jar
- trustedx-client-axis-stub.jar
- trustedx-client-axis.jar
- trustedx-provider.jar
- activation.jar
- axis.jar

Durant la compilació, aquest arxiu només és necessari per codificar i descodificar valors en Base64 mitjançant la classe org.apache.axis.encoding.Base64.

- commons-discovery-0.2.jar
- commons-httpclient-3.0.1.jar
- commons-logging-1.0.4.jar
- jaxrpc.jar
- log4j-1.2.8.jar
- saaj.jar
- wsdl4j-1.5.1.jar
- xercesImpl.jar
- xml-apis.jar
- commons-collections-3.2.jar
- commons-configuration.jar
- commons-lang-2.6.jar
- sfly-ssl.jar

## 3.5Arxiu smartwrapper.properties

El directori des d&#39;on s&#39;executi el client, haurà d&#39;incloure l&#39;arxiu de configuració **smartwrapper.properties**.

La següent taula defineix els paràmetres inclosos en l&#39;arxiu smartwrapper.properties:

| Paràmetre | Valor |
| --- | --- |
| Truststore.active | true: per la connexió HTTP es farà servir el magatzem de certificats definit al paràmetre Truststore.path. false (valor por defecte): s&#39;utilitzarà el magatzem de certificats configurat en la màquina virtual de Java (si n&#39;hi ha). |
| Truststore.path | Magatzem de certificats que s&#39;utilitzarà a la connexió HTTP (si el valor de Truststore.active és true). |
| Comptabilitzada l&#39;obligació reconeguda | Contrasenya del magatzem de certificats definit a Truststore.path. |
| Pagada | true: per la connexió HTTPS s&#39;utilitzarà el magatzem de claus definit al paràmetre Keystore.path.false (valor por defecte): s&#39;utilitzarà el magatzem de claus configurat en a màquina virtual de Java (si n&#39;hi ha). |
| Keystore.path | Magatzem de claus utilitzat en la connexió HTTPS (si el valor de keystore.active és true). |
| Keystore.password | Contrasenya del magatzem de claus definit a Keystore.path. |
| Keystore.Type | Tipus de keystore: JKS (valor per defecte), JCEKS, o PKCS12 |
| Proxy.active | true: per la connexió HTTP s&#39;utilitzarà un servidor Proxy.false: no s&#39;utilitzarà un servidor proxy. |
| Proxy.host | Servidor proxy utilitzat (si proxy.active és true). |
| Proxy.port | Port del servidor proxy. |
| Proxy.username | Nom d&#39;usuari per accedir al servidor proxy (si requereix autenticació HTTP bàsica). |
| Proxy.password | Contrasenya per accedir al servidor proxy (si requereix autenticació HTTP bàsica). |
| Timeout | Temps d&#39;espera de la connexió HTTP (en mil·lisegons). |
| Request.loadPath | Directori base dels arxius creats per enviar amb les peticions quan es maneguen dades de gran tamany. |
| Response.savePath | Directori base dels arxius creats en rebre les respostes quan es maneguen dades de gran tamany. |
| req-log.active | true: las peticions SOAP enviades es guardaran en arxius de log.false (valor por defecte): les peticions SOAP enviades no es guardaran en arxius de log. |
| req-log.savePath | Directori on es guardaran els arxius de log amb les peticions enviades (si el valor de req-log.active és true). |
| res-log.active | true: es guardaran arxius de log amb el contingut de les respostes rebudes.false (valor por defecte): no se guardaran arxius de log amb el contingut de les respostes rebudes. |
| res-log.savePath | Directori on es guardaran els arxius de log amb les respostes rebudes (si el valor de res-log.active és true). |
| authN.policy | Política d&#39;autenticació sol·licitada (opcional). |
| Ssl.allowCriticalExts | true: durant la connexió SSL es permeten certificats de servidor amb qualsevol extensió marcada com a crítica.false (valor per defecte): durant la connexió SSL no es permeten certificats de servidor amb extensions crítiques. |
| Ssl.noValidation | true: s&#39;anul·la la validació del certificat del servidor durant les connexions SSL.false (valor per defecte): es valida el certificat del servidor durant les connexions SSL. |
| Ssl.validation | Algorisme per validar el certificat del servidor durant connexions SSL. L&#39;algorisme utilitzat ha d&#39;estar implementat per un proveïdor criptogràfic registrat. |

# 4Serveis de Signatura

En aquest capítol explicarem, fent ús de casos pràctics, com accedir als serveis de creació de signatura mitjançant SmartWrapper.

En tots aquests exemples farem servir l&#39;autenticació de client mitjançant certificat. A tal efecte, caldrà configurar l&#39;arxiu smartwrapper.properties amb les dades del keystore i el truststore. Pels exemples farem servir el keystore i el truststore de proves que distribuïm dins el pack d&#39;integració:

# truststore

Truststore.active = true

Truststore.path = resources/truststore/catcert.truststore

Truststore.password = catcert

# keystore

Keystore.active = true

Keystore.path = resources/keystore/apptest/20100428\_111540\_CDA\_1\_cda\_c1\_policy.p12

Keystore.password = 1234

Keystore.type = PKCS12

## 4.1Signatura CMS attached

Amb el codi següent enviem una petició SOAP de creació d&#39;una signatura CMS attached (adjunta), i consultem la resposta obtinguda.

import com.safelayer.trustedx.client.smartwrapper.\*;

import org.apache.axis.encoding.Base64;

import org.apache.axis.message.SOAPHeaderElement;

publicclass CmsSignature {

staticfinal String _TRUSTEDX\_URL_ = &quot;https://ssc.preproduccio.catcert.cat:8443/trustedx-sgw/SignCert&quot;;

staticfinal String _SIGNER\_DN_ = &quot;CN=Dummy&quot;;

staticfinal String _RESULTMAJOR\_SUCCESS_ = &quot;urn:oasis:names:tc:dss:1.0:resultmajor:Success&quot;;

staticfinal String _DIPOSITARI_ = &quot;O=0000000000&quot;;

staticfinal String _ROL_ = &quot;TEST&quot;;

publicstaticbyte[] signCms(byte[] dataToSign) throws Exception {

SmartSignRequest sReq = new SmartSignRequest(_TRUSTEDX\_URL_);

//afegeixlacapçalera a lapetició

Stub stub = (Stub) sReq.getStub();

stub.setHeader(null, &quot;Rol&quot;, ROL);

stub.setHeader(null, &quot;Dipositari&quot;, DIPOSITARI);

//signatura CMS

sReq.setProfile(Constants.Profile._CMSPKCS7_);

//signatura attached

sReq.setEnvelopingSignature(true);

//dades a signar

sReq.setInputBase64Data(Base64._encode_(dataToSign));

//selecciódelaclaudesignatura

sReq.setKeySubjectName(_SIGNER\_DN_);

//enviamentdelapetició

SmartSignResponse sResp = sReq.send();

if (_RESULTMAJOR\_SUCCESS_.equals(sResp.getResultMajor())

&amp;&amp; sResp.getResultMinor() == null) {

//recuperaciódelasignatura

String signatureBase64 = sResp.getSignatureBase64();

return Base64._decode_(signatureBase64);

} else {

thrownew Exception(&quot;Error signing:&quot; + sResp.getResultMessage());

}

}

publicstaticvoid main(String args[]) throws Exception {

String data = &quot;data to sign...&quot;;

byte[] signature = _signCms_(data.getBytes());

}

}

Per construir la petició, invoquem els mètodes de la classe SmartSignRequest i SmartHeader descrits a la taula següent:

La classe SmartHeader permet afegir paràmetres al element Header de la petició SOAP. Aquesta classe es comporta igual a tots els següents exemples.

| Mètode | Paràmetres | Mètode | Paràmetres |
| --- | --- | --- | --- |
| getStub | Obté l&#39;objecte Stub de baix nivell Axis. | getStub | Obté l&#39;objecte Stub de baix nivell Axis. |
| setHeader | Afegeix l&#39;element al node Header. | setHeader | Afegeix l&#39;element al node Header. |

D&#39;altra banda, la classe SmartSignRequest construeix l&#39;element Body de la petició SOAP.

| Mètode | Paràmetres |
| --- | --- |
| setProfile | Constants.Profile.CMSPKCS7 per seleccionar el tipus de signatura CMS/PKCS#7. |
| setEnvelopingSignature | true per signatura attached (adjunta). |
| setInputBase64Data | Dades a signar, codificades en Base64. |

Amb els mètodes de la classe SmartSignResponse obtenim la resposta a la nostra petició de signatura:

| Mètode | Paràmetres |
| --- | --- |
| getResultMajor | Indica si s&#39;ha pogut processar la petició, independentment del resultat d&#39;aquesta. |
| getResultMinor | Detalls de la operació. |
| getSignatureBase64 | Signatura CMS codificada en Base64. |

##


## 4.2Signatura XML enveloped

Amb el codi següent enviem una petició SOAP de creació d&#39;una signatura XML enveloped (embolcallada), i consultem la resposta obtinguda.

import com.safelayer.trustedx.client.smartwrapper.\*;

import org.apache.axis.encoding.Base64;

import org.apache.axis.message.SOAPHeaderElement;

publicclass XmlEnvelopedSignature {

staticfinal String _TRUSTEDX\_URL_ = &quot;https://ssc.preproduccio.catcert.cat:8443/trustedx-sgw/SignCert&quot;;

staticfinal String _SIGNER\_DN_ = &quot;CN=Dummy&quot;;

staticfinal String _RESULTMAJOR\_SUCCESS_ = &quot;urn:oasis:names:tc:dss:1.0:resultmajor:Success&quot;;

staticfinal String _DIPOSITARI_ = &quot;O=0000000000&quot;;

staticfinal String _ROL_ = &quot;TEST&quot;;

publicstaticbyte[] signEnvelopedXml(byte[] dataToSign) throws Exception {

SmartSignRequest sReq = new SmartSignRequest(_TRUSTEDX\_URL_);

//afegeixlacapçalera a lapetició

Stub stub = (Stub) sReq.getStub();

stub.setHeader(null, &quot;Rol&quot;, ROL);

stub.setHeader(null, &quot;Dipositari&quot;, DIPOSITARI);

//signatura XML simple

sReq.setProfile(Constants.Profile._XADES_);

sReq.setSignatureFormat(Constants.SignatureFormat._NOADES_);

//signatura enveloped

sReq.setSignaturePlacement(Constants.SignaturePlacement._ENVELOPED_);

//posicionamentdelasignaturadins el document

sReq.setXmlEnvelopedXPathFirstChildOf(&quot;/&quot;);

//dades a signar

sReq.setInputXmlBase64(Base64._encode_(dataToSign));

//selecciódelaclaudesignatura

sReq.setKeySubjectName(_SIGNER\_DN_);

//enviamentdelapetició

SmartSignResponse sResp = sReq.send();

if (_RESULTMAJOR\_SUCCESS_.equals(sResp.getResultMajor())

&amp;&amp; sResp.getResultMinor() == null) {

//recuperaciódelasignatura

String signature = sResp.getDocumentWithSignatureXml();

return signature.getBytes();

} else {

thrownew Exception(&quot;Error signing:&quot; + sResp.getResultMessage());

}

}

publicstaticvoid main(String args[]) throws Exception {

String data = &quot;\&lt;library Id=&#39;c123tpe4ryta6di24&#39;\&gt;&quot;

+&quot;\&lt;book Id=&#39;1&#39;\&gt;&quot;

+&quot; \&lt;title\&gt;The dark house\&lt;/title\&gt;&quot;

+&quot;\&lt;/book\&gt;&quot;

+&quot;\&lt;book Id=&#39;2&#39;\&gt;&quot;

+&quot; \&lt;title\&gt;The laundry\&lt;/title\&gt;&quot;

+&quot;\&lt;/book\&gt;&quot;

+&quot;\&lt;/library\&gt;&quot;;

byte[] signature = _signEnvelopedXml_(data.getBytes());

System._out_.println(&quot;signature=&quot; + new String(signature));

}

}

Per construir la petició, invoquem els mètodes de la classe SmartSignRequest descrits a la taula següent:

| Mètode | Paràmetres |
| --- | --- |
| setProfile | Constants.Profile.XADES per seleccionar el perfil de signatura XML (tant per signatures simples com avançades). |
| setSignatureFormat | Format de la signatura. Pot tenir els següents valors:Signatura simple:Constants.SignatureFormat.NOADESSignatura AdES-BES:Constants.SignatureFormat.BESSignatura AdES-T:Constants.SignatureFormat.ES\_TSignatura AdES-C:Constants.SignatureFormat.ES\_CSignatura AdES-A:Constants.SignatureFormat.ES\_A |
| setSignaturePlacement | Constants.SignaturePlacement.ENVELOPED per seleccionar el tipus de signatura XML enveloped. Per seleccionar una signatura detached, farem servir el següent paràmetre: Constants.SignaturePlacement.DETACHED I per seleccionar una signatura del tipus enveloping, farem servir el paràmetre: Constants.SignaturePlacement.ENVELOPING |
| setXmlEnvelopedXPathFirstChildOf | Expressió XPath que indica on volem que s&#39;incrusti la signatura generada. Per exemple, &quot;/&quot; per ubicar la signatura a continuació del node arrel del document XML. |
| setXmlReturnBase64 | true per obtenir la signatura codificada en Base64 (i evitar així problemes amb Axis a l&#39;hora de serialitzar i deserialitzar signatures XML). |
| setKeySubjectName | Certificat amb el que generar la signatura. |
| setInputXmlBase64 | Dades a signar, codificades en Base64. |

Amb els mètodes de la classe SmartSignResponse obtenim la resposta a la nostra petició de signatura:

| Mètode | Paràmetres |
| --- | --- |
| getResultMajor | Indica si s&#39;ha pogut processar la petició, independentment del resultat d&#39;aquesta. |
| getResultMinor | Detalls de la operació. |
| getDocumentWithSignatureXml | Signatura XML. |
| getDocumentWithSignatureXmlBase64 | Signatura XML codificada en Base64. |

## 4.3Signatura XAdES-T detached a partir del hash d&#39;un document

![Shape8](RackMultipart20220630-1-6kytqz_html_b3b4b667748d1a1.gif)

import com.safelayer.trustedx.client.smartwrapper.\*;

importorg.apache.axis.encoding.Base64;

import org.apache.axis.message.SOAPHeaderElement;

publicclass XAdESTDetachedSignature {

staticfinal String _TRUSTEDX\_URL_ = &quot;https://ssc.preproduccio.catcert.cat:8443/trustedx-sgw/SignCert&quot;;

staticfinal String _SIGNER\_DN_ = &quot;CN=Dummy&quot;;

staticfinal String _RESULTMAJOR\_SUCCESS_ = &quot;urn:oasis:names:tc:dss:1.0:resultmajor:Success&quot;;

staticfinal String _DIPOSITARI_ = &quot;O=0000000000&quot;;

staticfinal String _ROL_ = &quot;TEST&quot;;

publicstaticbyte[] signDetachedXAdEST(byte[] dataToSign) throws Exception {

SmartSignRequest sReq = new SmartSignRequest(_TRUSTEDX\_URL_);

//afegeixlacapçalera a lapetició

Stub stub = (Stub) sReq.getStub();

stub.setHeader(null, &quot;Rol&quot;, ROL);

stub.setHeader(null, &quot;Dipositari&quot;, DIPOSITARI);

//signatura XML simple

sReq.setProfile(Constants.Profile._XADES_);

sReq.setSignatureFormat(Constants.SignatureFormat._ES\_T_);

//dades a signar

sReq.setInputHashDigest(dataToSign.toString());

sReq.setInputHashAlgorithm(&quot;sha1&quot;);

//selecciódelaclaudesignatura

sReq.setKeySubjectName(_SIGNER\_DN_);

//enviamentdelapetició

SmartSignResponse sResp = sReq.send();

if (_RESULTMAJOR\_SUCCESS_.equals(sResp.getResultMajor())

&amp;&amp; sResp.getResultMinor() == null) {

//recuperaciódelasignatura

String signature = sResp.getSignatureXml();

return signature.getBytes();

} else {

throw new Exception(&quot;Error signing:&quot; + sResp.getResultMessage());

}

}

public static void main(String args[]) throws Exception {

String data = &quot;gYbYj9w6DofPvCfwqKKwXitsErA=&quot;;

byte[] signature = signDetachedXAdEST(data.getBytes());

System.out.println(&quot;signature=&quot; + new String(signature));

}

}

En aquest cas, exposem codi d&#39;exemple per generar una signatura XML avançada amb segell de temps, a partir del resum criptogràfic (hash) d&#39;un document.

Per construir la petició, invoquem els mètodes:

| Mètode | Paràmetres |
| --- | --- |
| setInputHashDigest | Hash de les dades a signar, codificat en Base64. |
| setInputHashAlgorithm | Algorisme de hash amb que s&#39;ha calculat el resum anterior |

## 4.4Signatura de documents PDF

Amb el codi següent enviem una petició de signatura d&#39;un document PDF, fent signatura visible, i consultem la resposta obtinguda.

**Important** : L&#39;SSC només suporta la signatura d&#39;arxius PDF que utilitzin la versió 1.5 del format PDF.

import com.safelayer.trustedx.client.smartwrapper.\*;

import java.io.\*;

import org.apache.axis.encoding.Base64;

import org.apache.axis.message.SOAPHeaderElement;

public class PdfSignature {

static final String TRUSTEDX\_URL = &quot;https://ssc.preproduccio.catcert.cat:8443/trustedx-sgw/SignCert&quot;;

static final String SIGNER\_DN = &quot;CN=Dummy&quot;;

static final String RESULTMAJOR\_SUCCESS = &quot;urn:oasis:names:tc:dss:1.0:resultmajor:Success&quot;;

static final String DIPOSITARI = &quot;O=0000000000&quot;;

static final String ROL = &quot;TEST&quot;;

public static byte[] signPdf(byte[] pdfToSign, String signatureInfo) throws Exception{

SmartSignRequest sReq = new SmartSignRequest(TRUSTEDX\_URL);

//afegeix la capçalera a la petició

Stub stub = (Stub) sReq.getStub();

stub.setHeader(null, &quot;Rol&quot;, ROL);

stub.setHeader(null, &quot;Dipositari&quot;, DIPOSITARI);

//signatura d&#39;un document PDF

sReq.setProfile(Constants.Profile.PDF);

//tipus de signatura

sReq.setSignatureType(Constants.SignatureType.CMS);

//selecció de la clau de signatura

sReq.setKeySubjectName(SIGNER\_DN);

//PDF a signar

sReq.setInputPdfBase64Data(Base64.encode(pdfToSign));

//configuració signatura visible

sReq.setPdfSignatureInfo(signatureInfo);

//enviament de la petició

SmartSignResponse sResp = sReq.send();

if (RESULTMAJOR\_SUCCESS.equals(sResp.getResultMajor()) &amp;&amp; sResp.getResultMinor() == null) {

return Base64.decode(sResp.getDocumentWithSignaturePdf());

} else {

throw new Exception(&quot;Error signing:&quot; + sResp.getResultMessage());

}

}

public static void main(String args[]) throws Exception {

String signatureInfo =

&quot;\&lt;css:PdfSignatureInfo xmlns:css=&#39;http://www.safelayer.com/TWS&#39;\&gt;&quot; +

&quot;\&lt;css:PdfAttributes\&gt;\&lt;css:signatureAlg\&gt;SHA1\&lt;/css:signatureAlg\&gt;&quot; +

&quot; \&lt;css:validationMethod\&gt;PPKMS\&lt;/css:validationMethod\&gt;&quot; +

&quot; \&lt;css:signaturePosition\&gt;ADDLAST\&lt;/css:signaturePosition\&gt;&quot; +

&quot; \&lt;css:params\&gt;\&lt;css:reason\&gt;Author\&lt;/css:reason\&gt;\&lt;/css:params\&gt;&quot; +

&quot;\&lt;/css:PdfAttributes\&gt;&quot; +

&quot;\&lt;css:Appearance\&gt;&quot; +

&quot; \&lt;css:Rect x0=&#39;100&#39; y0=&#39;50&#39; x1=&#39;520&#39; y1=&#39;150&#39;/\&gt;&quot; +

&quot; \&lt;css:Background\&gt;\&lt;css:image encodeType=&#39;base64&#39;\&gt;&quot; +

&quot;\&lt;css:data\&gt;/9j/4AAQSkZJRgABAQEAYABgAAD/4QAWRXhpZgAASUkqAAgAAAAAAAAAAAD/2wBD&quot; +

&quot;AAgGBgcGBQgHBwcJCQgKDBQNDAsLDBkSEw8UHRofHh0aHBwgJC4nICIsIxwcKDcpLDAxNDQ0Hy&quot; +

&quot;c5PTgyPC4zNDL/2wBDAQkJCQwLDBgNDRgyIRwhMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjIy&quot; +

&quot;MjIyMjIyMjIyMjIyMjIyMjIyMjIyMjL/wAARCAB+AMcDASIAAhEBAxEB/8QAHwAAAQUBAQEBAQ&quot; +

&quot;EAAAAAAAAAAAECAwQFBgcICQoL/8QAtRAAAgEDAwIEAwUFBAQAAAF9AQIDAAQRBRIhMUEGE1Fh&quot; +

&quot;ByJxFDKBkaEII0KxwRVS0fAkM2JyggkKFhcYGRolJicoKSo0NTY3ODk6Q0RFRkdISUpTVFVWV1&quot; +

&quot;hZWmNkZWZnaGlqc3R1dnd4eXqDhIWGh4iJipKTlJWWl5iZmqKjpKWmp6ipqrKztLW2t7i5usLD&quot; +

&quot;xMXGx8jJytLT1NXW19jZ2uHi4+Tl5ufo6erx8vP09fb3+Pn6/8QAHwEAAwEBAQEBAQEBAQAAAA&quot; +

&quot;AAAAECAwQFBgcICQoL/8QAtREAAgECBAQDBAcFBAQAAQJ3AAECAxEEBSExBhJBUQdhcRMiMoEI&quot; +

&quot;FEKRobHBCSMzUvAVYnLRChYkNOEl8RcYGRomJygpKjU2Nzg5OkNERUZHSElKU1RVVldYWVpjZG&quot; +

&quot;VmZ2hpanN0dXZ3eHl6goOEhYaHiImKkpOUlZaXmJmaoqOkpaanqKmqsrO0tba3uLm6wsPExcbH&quot; +

&quot;yMnK0tPU1dbX2Nna4uPk5ebn6Onq8vP09fb3+Pn6/9oADAMBAAIRAxEAPwD3+iiigAooooAKKK&quot; +

&quot;KACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAqOeeO2t5biZtkUSF3Y&quot; +

&quot;9lAyTT6z/EH/ACLeqf8AXnL/AOgGgFuUx4w0MjP2qX/wFl/+Jo/4TDQ/+fqX/wABZf8A4muWjk&quot; +

&quot;8u3QseAgyeuOM9qT7TGSMllz03Arkfj/XFc3t32PSWATSdzqv+Ex0P/n6l/wDAWX/4mj/hMdD/&quot; +

&quot;AOfqX/wFl/8Aia5rP+cmkyN3X+dSsT5F/wBnLudOPF+iEgC6lyen+jS//E1Z/t/T/wC9cf8AgL&quot; +

&quot;L/APE1xx5K45w68+nzD/GvQl+7W9OfOcWIoexlYzv7f0/+9cf+Asv/AMTR/b+n/wB64/8AAWX/&quot; +

&quot;AOJrRoyM1oc5nf2/p/8AeuP/AAFl/wDiadHrunyOiCSVS7BF328igknAGStX+veszWcCG1P/AE&quot; +

&quot;+Qfn5goA1aKKKACiiigAooooAKKKKACiiigAooooAKKKKAErP8Qf8AIt6p/wBecv8A6Aa0O9Z+&quot; +

&quot;v/8AIt6p/wBekv8A6AaXQFucE4DC2Rzhdh2k9A2Bg/WobbbAWtbuJUkERJkXpIAeT9elXURZLW&quot; +

&quot;NSMqVBx74pFtYVbd5YJxj5jmuBux9ByXSsUlOshFwbYj/aznFQ3t3qdlbtPKLbapA4z36VsEf5&quot; +

&quot;zSFFfh0DDsDyKSlrsU6btuyvZyTS2kUlx5ZZmRgE/ulhXcl9S/fbY4mwf3eeOM/4Vx2BhQBgBl&quot; +

&quot;HTHGRXoKgbRXVQd4s8vHL3kUXN+NzKsePMAC+i45P1zSyy3oRhHEhcMPmJwCuf54q9jjFGOtbn&quot; +

&quot;CUma/wDNTaI9vmENx/D2qjfm6MMQuggH22Ax49PMFbh+tZesnMVqMZ/0yD/0MUAatFFFABRRRQ&quot; +

&quot;AUUUUAFFFFABRRRQAUUUUAFFFFABUF7bLe2FxaMxVZ4mjLDqAwIz+tT0UAc2PCQCgDUp8AYHyL&quot; +

&quot;0/Kl/wCEU/6iM3/ftP8ACujoqPZx7Gvt6nc5z/hE/wDqJTf9+0/wo/4RT/qJT/8AftP8K6LNLm&quot; +

&quot;j2cew/rFX+Y53/AIRRSQTqE5wQfuL/AIVr/Zbn/n+f/v2v+FW6M1SSWiM5zlN3kyp9muf+f5/+&quot; +

&quot;/a/4UfZrn/n+f/v2v+FW6KZJU+y3X/P+/wD37X/CoZdNkuDF594zrHKkoGwDlTmtGigAooooAK&quot; +

&quot;KKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACkOaKX3oAiuJktoGlc4VRk&quot; +

&quot;1zMWrX1/rUCRNsiznZjqueSfw/nTvEF/51wLWN/3acyY7n0qTwvZkyT3r9ztjz2Hf+WPwrPnbl&quot; +

&quot;ZHV7JRpc73OlopD1pa0OUKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKA&quot; +

&quot;CqmpXYsrGWY/eAwo9W7CrVYGsebqOqQadCflX55G/u/5B/Wk9tCoK71KWi6e99dNcTZMSOST2d&quot; +

&quot;u/4Zrq0RY1CooVR2FMtreO1t0hjGEQYFSmlGPKiqtRzlcO9FAoqjMKKKKACiiigAooooAKKKKA&quot; +

&quot;CiiigAooooAKKKKACiiigAooooAKKKKAENU9PtDAsk8nM9w2+Q+noPwHFXCKWgAooooAKKKKAC&quot; +

&quot;iiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooA&quot; +

&quot;KKKKACiiigAooooAKKKKACiiigD/2Q==\&lt;/css:data\&gt;&quot; +

&quot; \&lt;css:imageSize width=&#39;200&#39; height=&#39;100&#39;/\&gt;&quot; +

&quot; \&lt;css:position x=&#39;0&#39; y=&#39;0&#39;/\&gt;\&lt;/css:image\&gt;\&lt;/css:Background\&gt;&quot; +

&quot; \&lt;css:Foreground\&gt;&quot; +

&quot; \&lt;css:image encodeType=&#39;base64&#39;\&gt;\&lt;css:data\&gt;/9j/4AAQSkZJRgABAQEAYABgAAD/2wBDAAgGBgcGBQgHB&quot; +

&quot;wcJCQgKDBQNDAsLDBkSEw8UHRofHh0aHBwgJC4nICIsIxwcKDcpLDAxNDQ0Hyc5PTgyPC4zNDL&quot; +

&quot;/2wBDAQkJCQwLDBgNDRgyIRwhMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjIyM&quot; +

&quot;jIyMjIyMjIyMjIyMjL/wAARCAABAAEDASIAAhEBAxEB/8QAHwAAAQUBAQEBAQEAAAAAAAAAAAE&quot; +

&quot;CAwQFBgcICQoL/8QAtRAAAgEDAwIEAwUFBAQAAAF9AQIDAAQRBRIhMUEGE1FhByJxFDKBkaEII&quot; +

&quot;0KxwRVS0fAkM2JyggkKFhcYGRolJicoKSo0NTY3ODk6Q0RFRkdISUpTVFVWV1hZWmNkZWZnaGl&quot; +

&quot;qc3R1dnd4eXqDhIWGh4iJipKTlJWWl5iZmqKjpKWmp6ipqrKztLW2t7i5usLDxMXGx8jJytLT1&quot; +

&quot;NXW19jZ2uHi4+Tl5ufo6erx8vP09fb3+Pn6/8QAHwEAAwEBAQEBAQEBAQAAAAAAAAECAwQFBgc&quot; +

&quot;ICQoL/8QAtREAAgECBAQDBAcFBAQAAQJ3AAECAxEEBSExBhJBUQdhcRMiMoEIFEKRobHBCSMzU&quot; +

&quot;vAVYnLRChYkNOEl8RcYGRomJygpKjU2Nzg5OkNERUZHSElKU1RVVldYWVpjZGVmZ2hpanN0dXZ&quot; +

&quot;3eHl6goOEhYaHiImKkpOUlZaXmJmaoqOkpaanqKmqsrO0tba3uLm6wsPExcbHyMnK0tPU1dbX2&quot; +

&quot;Nna4uPk5ebn6Onq8vP09fb3+Pn6/9oADAMBAAIRAxEAPwD3+iiigD//2Q==\&lt;/css:data\&gt;&quot; +

&quot; \&lt;css:imageSize width=&#39;1&#39; height=&#39;1&#39;/\&gt;&quot; +

&quot; \&lt;css:position x=&#39;0&#39; y=&#39;0&#39;/\&gt;\&lt;/css:image\&gt;&quot; +

&quot; \&lt;css:text\&gt;\&lt;css:properties color=&#39;0 0 0&#39; fontSize=&#39;10&#39;/\&gt;&quot; +

&quot; \&lt;css:position x=&#39;12&#39; y=&#39;12&#39;/\&gt;&quot; +

&quot; \&lt;css:SignatureInfos\&gt;&quot; +

&quot; \&lt;css:signatureInfo title=&#39; &#39; id=&#39;Subject&#39;/\&gt;&quot; +

&quot; \&lt;css:signatureInfo title=&#39; &#39; id=&#39;Date&#39;/\&gt;&quot; +

&quot; \&lt;/css:SignatureInfos\&gt;\&lt;/css:text\&gt;\&lt;/css:Foreground\&gt;&quot; +

&quot; \&lt;/css:Appearance\&gt;\&lt;/css:PdfSignatureInfo\&gt;&quot;;

//lectura del document PDF

File file = new File(&quot;unsigned.pdf&quot;);

FileInputStream fis = new FileInputStream(file);

byte[] pdfToSign = new byte[(int)file.length()];

fis.read(pdfToSign);

fis.close();

byte[] signature = signPdf(pdfToSign, signatureInfo);

//guardem el PDF signat en un fitxer

java.io.FileOutputStream fos = new java.io.FileOutputStream(&quot;signed.pdf&quot;);

if (fos!=null) {

fos.write(signature);

fos.close();

}

}

}

Per construir la petició, invoquem els mètodes de la classe SmartSignRequest descrits a la taula següent:

| Mètode | Paràmetres |
| --- | --- |
| setProfile | Constants.Profile.PDF per seleccionar el perfil de signatura PDF. |
| setSignatureType | Format de la signatura: Constants.SignatureType.CMS |
| setPdfSignatureInfo | Tipus de signatura desitjat. En aquest exemple incloem informació de l&#39;aparença de la signatura per tal que sigui visible. |
| setInputPdfBase64Data | Document PDF a signar codificat en Base64. |

### 4.4.1Paràmetres de signatura visible

Passarem a descriure els diferents paràmetres que permeten la configuració de la signatura visible en documents PDF.

#### 4.4.1.1Element \&lt;css:PdfSignatureInfo\&gt;

Aquest element conté informació sobre els atributs de signatura propis d&#39;Adobe. L&#39;estructura d&#39;aquest element és la següent:

\&lt;xs:element name=&quot;PdfSignatureInfo&quot; type=&quot;css:PdfSignatureInfoType&quot; maxOccurs=&quot;unbounded&quot;/\&gt;

\&lt;xs:complexType name=&quot;PdfSignatureInfoType&quot;\&gt;

\&lt;xs:all\&gt;

\&lt;xs:element name=&quot;PdfAttributes&quot; type=&quot;css:PdfAttributesType&quot;/\&gt;

\&lt;xs:element name=&quot;Appearance&quot; type=&quot;css:AppearanceType&quot; minOccurs=&quot;0&quot;/\&gt;

\&lt;/xs:all\&gt;

\&lt;xs:attribute name=&quot;name&quot; type=&quot;xs:string&quot; use=&quot;optional&quot;/\&gt;

\&lt;xs:attribute name=&quot;order&quot; type=&quot;xs:integer&quot; use=&quot;optional&quot;/\&gt;

\&lt;/xs:complexType\&gt;

On podem observat que l&#39;element \&lt;css:PdfSignatureInfo\&gt; inclou els següents elements:

- \&lt;css:PdfAttributes\&gt;: Configuració del mode de signatura.

- \&lt;css:Appearance\&gt; [Opcional]. Paràmetres de l&#39;aparença de la signatura. Si aquest element no està present, es genera una signatura de tipus invisible.

**Element \&lt;css:PdfAttributes\&gt;**

L&#39;element \&lt;css:PdfAttributes\&gt; es pot fer servir en dos contexts bàsics:

- Configuració dels paràmetres relacionats amb el mode de signatura.
- Obtenció d&#39;informació sobre el mode de signatura en operacions de verificació.

La seva definició és la següent:

\&lt;xs:element name=&quot;PdfAttributes&quot; type=&quot;css:PdfAttributesType&quot;/\&gt;

\&lt;xs:complexType name=&quot;PdfAttributesType&quot;\&gt;

\&lt;xs:sequence\&gt;

\&lt;xs:element name=&quot;certified&quot; minOccurs=&quot;0&quot;\&gt;

\&lt;xs:simpleType\&gt;

\&lt;xs:restriction base=&quot;xs:integer&quot;\&gt;

\&lt;xs:enumeration value=&quot;0&quot;/\&gt;

\&lt;xs:enumeration value=&quot;1&quot;/\&gt;

\&lt;xs:enumeration value=&quot;2&quot;/\&gt;

\&lt;/xs:restriction\&gt;

\&lt;/xs:simpleType\&gt;

\&lt;/xs:element\&gt;

\&lt;xs:element name=&quot;signatureAlg&quot;\&gt;

\&lt;xs:simpleType\&gt;

\&lt;xs:restriction base=&quot;xs:string&quot;\&gt;

\&lt;xs:enumeration value=&quot;SHA1&quot;/\&gt;

\&lt;xs:enumeration value=&quot;DETACHED&quot;/\&gt;

\&lt;/xs:restriction\&gt;

\&lt;/xs:simpleType\&gt;

\&lt;/xs:element\&gt;

\&lt;xs:element name=&quot;validationMethod&quot;\&gt;

\&lt;xs:simpleType\&gt;

\&lt;xs:restriction base=&quot;xs:string&quot;\&gt;

\&lt;xs:enumeration value=&quot;PPKMS&quot;/\&gt;

\&lt;xs:enumeration value=&quot;PPKLITE&quot;/\&gt;

\&lt;/xs:restriction\&gt;

\&lt;/xs:simpleType\&gt;

\&lt;/xs:element\&gt;

\&lt;xs:element name=&quot;signaturePosition&quot;\&gt;

\&lt;xs:simpleType\&gt;

\&lt;xs:restriction base=&quot;xs:string&quot;\&gt;

\&lt;xs:enumeration value=&quot;FIRST&quot;/\&gt;

\&lt;xs:enumeration value=&quot;LAST&quot;/\&gt;

\&lt;xs:enumeration value=&quot;ADDLAST&quot;/\&gt;

\&lt;/xs:restriction\&gt;

\&lt;/xs:simpleType\&gt;

\&lt;/xs:element\&gt;

\&lt;xs:element name=&quot;params&quot; minOccurs=&quot;0&quot;\&gt;

\&lt;xs:complexType\&gt;

\&lt;xs:sequence\&gt;

\&lt;xs:element name=&quot;location&quot; type=&quot;xs:string&quot; minOccurs=&quot;0&quot;/\&gt;

\&lt;xs:element name=&quot;reason&quot; type=&quot;xs:string&quot; minOccurs=&quot;0&quot;/\&gt;

\&lt;xs:element name=&quot;contactInfo&quot; type=&quot;xs:string&quot; minOccurs=&quot;0&quot;/\&gt;

\&lt;/xs:sequence\&gt;

\&lt;/xs:complexType\&gt;

\&lt;/xs:element\&gt;

\&lt;/xs:sequence\&gt;

\&lt;/xs:complexType\&gt;

On es pot observar que l&#39;element \&lt;css:PdfAttributes\&gt; conté una seqüència dels següents elements, que veurem tot seguit:

- \&lt;css:signatureAlg\&gt;
- \&lt;css:validationMethod\&gt;
- \&lt;css:signaturePosition\&gt;
- \&lt;css:params\&gt; [Opcional]

**Element \&lt;css:signatureAlg\&gt;**

Indica el tipus de signatura PDF. La següent taula descriu els valors suportats per aquest element:

| Valor | Tipus de signatura |
| --- | --- |
| SHA1 | Signatura PKCS#7 attached sobre un resum criptogràfic SHA1 de les dades del PDF (adbe.pkcs7.sha1) |
| DETACHED | Signatura PKCS#7 detached sobre les dades d&#39;un PDF (adbe.pkcs7.detached). Adobe recomana utilitzar l&#39;algorisme DETACHED per a un millor compliment dels estàndards. |

**Element \&lt;css:validationMethod\&gt;**

Selecciona el plug-in amb el que validar la signatura PDF en AdobeReader. La següent taula descriu els valors suportats per aquest element:

| Valor | Tipus de signatura |
| --- | --- |
| PPKMS | Validador de Microsoft |
| PPKLITE | Validador d&#39;Adobe |

**Element \&lt;css:signaturePosition\&gt;**

Indica el posicionament de l&#39;aparença de la signatura. La següent taula descriu els valors suportats per aquest element:

| Valor | Tipus de signatura |
| --- | --- |
| FIRST | Validador de Microsoft |
| LAST | Validador d&#39;Adobe |
| ADDLAST | Pàgina afegida expressament al final del document. |

**Element \&lt;css:params\&gt;**

Defineix les propietats d&#39;una signatura PDF (que corresponen a entrades del seu diccionari) mitjançant els següents elements:

- \&lt;css:location\&gt;: Lloc de la signatura, indicat mitjançant una cadena de text. Correspon a l&#39;entrada de clau _Location_ del diccionari de la signatura.
- \&lt;css:reason\&gt;: Compromís de signatura, indicat mitjançant una cadena de text. Correspon a l&#39;entrada de clau _Reason_ del diccionari de signatura.
- \&lt;css:contactInfo\&gt;: Informació de contacte del signatari (p.ex. el seu número de telèfon), indicat mitjançant una cadena de text. Correspon a l&#39;entrada de clau _ContactInfo_ del diccionari de signatura.

**Exemple d&#39;element \&lt;css:PdfAttributes\&gt;**

\&lt;css:PdfAttributes\&gt;

\&lt;css:validationMethod\&gt;PPKMS\&lt;/css:validationMethod\&gt;

\&lt;css:signatureAlg\&gt;SHA1\&lt;/css:signatureAlg\&gt;

\&lt;css:signaturePosition\&gt;LAST\&lt;/css:signaturePosition\&gt;

\&lt;css:params\&gt;

\&lt;css:location\&gt;Barcelona\&lt;/css:location\&gt;

\&lt;css:reason\&gt;Razon de la firma\&lt;/css:reason\&gt;

\&lt;css:contactInfo\&gt;+34 555 666 777\&lt;/css:contactInfo\&gt;

\&lt;/css:params\&gt;

\&lt;/css:PdfAttributes\&gt;

**Element \&lt;css:Appearance\&gt;**

Defineix el format de l&#39;aparença de la signatura. Si aquest element no està present, es genera una signatura invisible.

L&#39;estructura d&#39;aquest element és la següent:

\&lt;xs:element name=&quot;Appearance&quot; type=&quot;css:AppearanceType&quot; minOccurs=&quot;0&quot;/\&gt;

\&lt;xs:complexType name=&quot;AppearanceType&quot;\&gt;

\&lt;xs:sequence\&gt;

\&lt;xs:element name=&quot;Rect&quot; type=&quot;css:RectType&quot; minOccurs=&quot;0&quot;/\&gt;

\&lt;xs:element name=&quot;Background&quot; type=&quot;css:BackgroundType&quot; minOccurs=&quot;0&quot;/\&gt;

\&lt;xs:element name=&quot;Foreground&quot; type=&quot;css:ForegroundType&quot; minOccurs=&quot;0&quot;/\&gt;

\&lt;/xs:sequence\&gt;

\&lt;/xs:complexType\&gt;

Conté els següents elements:

- \&lt;css:Rect\&gt;: Espai on s&#39;incrustarà l&#39;aparença si és necessari crear un nou camp de signatura. Si es treballa amb un camp de signatura buit, aquest element no té cap efecte.

- \&lt;css:Background\&gt;: Imatge de fons de l&#39;aparença de la signatura.
- \&lt;css:Foreground\&gt;: Imatge en primer pla de l&#39;aparença de la signatura.

**Element \&lt;css:Rect\&gt;**

L&#39;element \&lt;css:Rect\&gt; indica on col·locar una signatura quan aquesta és visible. La seva definició és la següent:

\&lt;xs:complexType name=&quot;RectType&quot;\&gt;

\&lt;xs:attribute name=&quot;x0&quot; type=&quot;xs:positiveInteger&quot;/\&gt;

\&lt;xs:attribute name=&quot;y0&quot; type=&quot;xs:positiveInteger&quot;/\&gt;

\&lt;xs:attribute name=&quot;x1&quot; type=&quot;xs:positiveInteger&quot;/\&gt;

\&lt;xs:attribute name=&quot;y1&quot; type=&quot;xs:positiveInteger&quot;/\&gt;

\&lt;/xs:complexType\&gt;

Els atributs x0, y0, x1, i y1 defineixen les coordenades del rectangle al que es mostra la signatura. Les coordenades origen (0,0) es situen a la cantonada inferior esquerra de la pàgina.

- x0, y0: Punt inferior esquerre (expressat en píxels)
- x1, y1: Punt superior dret (expressat en píxels)

**Element \&lt;css:Background\&gt;**

L&#39;element \&lt;css:Background\&gt; defineix la imatge de fons (en segon pla) d&#39;una signatura visible. La seva definició és:

\&lt;xs:element name=&quot;Background&quot; type=&quot;css:BackgroundType&quot;/\&gt;

\&lt;xs:complexType name=&quot;BackgroundType&quot;\&gt;

\&lt;xs:all\&gt;

\&lt;xs:element name=&quot;image&quot; type=&quot;css:ImageType&quot;/\&gt;

\&lt;/xs:all\&gt;

\&lt;/xs:complexType\&gt;

L&#39;element \&lt;css:Background\&gt; només conté l&#39;element \&lt;css:image\&gt;, que descriurem més endavant.

**Element \&lt;css:Foreground\&gt;**

L&#39;element \&lt;css:Foreground\&gt; defineix la imatge (en primer pla) i el text de la signatura. La seva definició és:

\&lt;xs:element name=&quot;Foreground&quot; type=&quot;css:ForegroundType&quot; minOccurs=&quot;0&quot;/\&gt;

\&lt;xs:complexType name=&quot;ForegroundType&quot;\&gt;

\&lt;xs:all\&gt;

\&lt;xs:element name=&quot;image&quot; type=&quot;css:ImageType&quot;/\&gt;

\&lt;xs:element name=&quot;text&quot; type=&quot;css:TextType&quot;/\&gt;

\&lt;/xs:all\&gt;

\&lt;/xs:complexType\&gt;

L&#39;element \&lt;css:Foreground\&gt; conté els dos elements següents:

- \&lt;css:image\&gt;: Imatge de la signatura.
- \&lt;css:text\&gt;: Text amb informació sobre la signatura.

**Element \&lt;css:image\&gt;**

L&#39;element \&lt;css:image\&gt; defineix la imatge d&#39;una signatura. La seva definició és:

\&lt;xs:element name=&quot;image&quot; type=&quot;css:ImageType&quot;/\&gt;

\&lt;xs:complexType name=&quot;ImageType&quot;\&gt;

\&lt;xs:all\&gt;

\&lt;xs:element name=&quot;data&quot; type=&quot;xs:string&quot;/\&gt;

\&lt;xs:element name=&quot;imageSize&quot; minOccurs=&quot;0&quot;\&gt;

\&lt;xs:complexType\&gt;

\&lt;xs:attribute name=&quot;width&quot; type=&quot;xs:positiveInteger&quot;/\&gt;

\&lt;xs:attribute name=&quot;height&quot; type=&quot;xs:positiveInteger&quot;/\&gt;

\&lt;/xs:complexType\&gt;

\&lt;/xs:element\&gt;

\&lt;xs:element name=&quot;position&quot; type=&quot;css:PositionType&quot; minOccurs=&quot;0&quot;/\&gt;

\&lt;/xs:all\&gt;

\&lt;xs:attribute name=&quot;encodeType&quot;\&gt;

\&lt;xs:simpleType\&gt;

\&lt;xs:restriction base=&quot;xs:string&quot;\&gt;

\&lt;xs:enumeration value=&quot;uri&quot;/\&gt;

\&lt;xs:enumeration value=&quot;base64&quot;/\&gt;

\&lt;/xs:restriction\&gt;

\&lt;/xs:simpleType\&gt;

\&lt;/xs:attribute\&gt;

\&lt;/xs:complexType\&gt;

L&#39;element \&lt;css:image\&gt; conté els següents atributs:

- //image/@encodeType: Indica la codificació utilitzada per l&#39;element \&lt;css:data\&gt; per definir la imatge de la signatura. La taula següent defineix els valors suportats per aquest atribut:

| Valor d&#39;encodeType | Contingut de \&lt;css:data\&gt; |
| --- | --- |
| uri | Referència al fitxer de la imatge |
| base64 | Imatge codificada en Base64 |

I els següents elements:

- \&lt;css:data\&gt;: Imatge de la signatura codificada de la manera que indica l&#39;atribut //image/@encodeType. El format de la imatge ha de ser JPEG.
- \&lt;css:imageSize\&gt;: Indica, mitjançant els següents atributs, el tamany de visualització de la imatge:

- //imageSize/@width: Amplada de la imatge (en píxels).

- //imageSize/@height: Alçada de la imatge (en píxels).

Si aquest element s&#39;omet, el tamany de visualització serà el real de la imatge.

- \&lt;css:Position\&gt;: Indica la posició relativa de la imatge dins l&#39;espai que defineix l&#39;element \&lt;css:Rect\&gt;. En concret, aquest element estableix la coordenada inferior esquerra de la imatge mitjançant els següents atributs:

- //position/@x: Desplaçament horitzontal (en píxels).

- //position/@y: Desplaçament vertical (en píxels).

**Element \&lt;css:text\&gt;**

L&#39;element \&lt;css:text\&gt; conté un text amb informació sobre la signatura. La definició és:

\&lt;xs:element name=&quot;text&quot; type=&quot;css:TextType&quot;/\&gt;

\&lt;xs:complexType name=&quot;TextType&quot;\&gt;

\&lt;xs:all\&gt;

\&lt;xs:element name=&quot;properties&quot; minOccurs=&quot;0&quot;\&gt;

\&lt;xs:complexType\&gt;

\&lt;xs:attribute name=&quot;color&quot; type=&quot;xs:string&quot;/\&gt;

\&lt;xs:attribute name=&quot;fontSize&quot; type=&quot;xs:positiveInteger&quot;/\&gt;

\&lt;/xs:complexType\&gt;

\&lt;/xs:element\&gt;

\&lt;xs:element name=&quot;position&quot; type=&quot;css:PositionType&quot; minOccurs=&quot;0&quot;/\&gt;

\&lt;xs:element name=&quot;SignatureInfos&quot; type=&quot;css:SignatureInfosType&quot; minOccurs=&quot;0&quot;/\&gt;

\&lt;/xs:all\&gt;

\&lt;/xs:complexType\&gt;

\&lt;xs:element name=&quot;SignatureInfos&quot; type=&quot;css:SignatureInfosType&quot; minOccurs=&quot;0&quot;/\&gt;

\&lt;xs:complexType name=&quot;SignatureInfosType&quot;\&gt;

\&lt;xs:sequence\&gt;

\&lt;xs:element name=&quot;signatureInfo&quot; maxOccurs=&quot;unbounded&quot;\&gt;

\&lt;xs:complexType\&gt;

\&lt;xs:attribute name=&quot;title&quot; type=&quot;xs:string&quot;/\&gt;

\&lt;xs:attribute name=&quot;id&quot;\&gt;

\&lt;xs:simpleType\&gt;

\&lt;xs:restriction base=&quot;xs:string&quot;\&gt;

\&lt;xs:enumeration value=&quot;Subject&quot;/\&gt;

\&lt;xs:enumeration value=&quot;Issuer&quot;/\&gt;

\&lt;xs:enumeration value=&quot;SerialNumber&quot;/\&gt;

\&lt;xs:enumeration value=&quot;Reason&quot;/\&gt;

\&lt;xs:enumeration value=&quot;Location&quot;/\&gt;

\&lt;xs:enumeration value=&quot;ContactInfo&quot;/\&gt;

\&lt;xs:enumeration value=&quot;Date&quot;/\&gt;

\&lt;/xs:restriction\&gt;

\&lt;/xs:simpleType\&gt;

\&lt;/xs:attribute\&gt;

\&lt;/xs:complexType\&gt;

\&lt;/xs:element\&gt;

\&lt;/xs:sequence\&gt;

\&lt;/xs:complexType\&gt;

L&#39;element \&lt;css.text\&gt; conté els següents elements:

- \&lt;css:properties\&gt; [Opcional] Defineix, mitjançant els següents atributs, el color i el tamany del text:

- //properties/@color: Color del text (en notació RGB, amb valors entre 0 i 1).

- //properties/@fontSize: Tamany de la font.

- \&lt;css:position\&gt; [Opcional] Indica la posició relativa del text dins l&#39;espai que defineix l&#39;element \&lt;css:Rect\&gt;. En concret, aquest element indica la coordenada inferior esquerra del text mitjançant els següents atributs:

- //position/@x: Desplaçament horitzontal (en píxels).

- //position/@y: Desplaçament vertical (en píxels).

- \&lt;css:SignatureInfos\&gt; [Opcional]: Inclou una seqüència d&#39;elements \&lt;css:SignatureInfo\&gt;, cadascun dels quals correspon a un camp textual que s&#39;integra en el text de la signatura, i té els següents atributs:

- //SignatureInfo/@title: Etiqueta que es mostra al costat del camp de text en la representació gràfica de la signatura.

- //SignatureInfo/@id: Identificador del camp de text. Aquest pot correspondre tant a camps del certificat (_Subject_, _Issuer_, _SerialNumber_), com a propietats de la signatura del PDF (_Reason_, _Location_, _ContactInfo_, _Date_) que estan contingudes al seu diccionari. Els valors que pot tenir són:

| Camp | Descripció |
| --- | --- |
| Subject | Titular del certificat de la signatura |
| Issuer | Autoritat de certificació (CA) que ha emès el certificat de la signatura |
| SerialNumber | Número de sèrie del certificat de la signatura |
| Reason | Raó de la generació de la signatura |
| Location | Lloc on s&#39;ha portat a terme la signatura |
| ContactInfo | Dades de contacte de la persona/entitat que ha realitzat al signatura |
| Date | Data de la signatura |

**Element \&lt;css:StoreSignatureField\&gt;**

Aquest element selecciona el camp de signatura al qual s&#39;ha d&#39;incrustar la signatura generada. La definició d&#39;aquest element és la següent:

\&lt;xs:element name=&quot;StoreSignatureField&quot;\&gt;

\&lt;xs:complexType\&gt;

\&lt;xs:attribute name=&quot;name&quot; type=&quot;xs:string&quot; use=&quot;required&quot;/\&gt;

\&lt;xs:attribute name=&quot;create&quot; type=&quot;xs:boolean&quot; use=&quot;required&quot;/\&gt;

\&lt;/xs:complexType\&gt;

\&lt;/xs:element\&gt;

L&#39;element \&lt;css:StoreSignatureField\&gt; conté els següents atributs:

- //StoreSignatureField/@name: Identificador del camp de signatura.
- //StoreSignatureField/@create: Booleà que indica si cal crear el camp de signatura indicat per //StoreSignatureField/@name, si no existeix al PDF.

#### 4.4.1.2Plantilla de signatures PDF

Una plantilla de signatura PDF és un document XML que té la següent estructura:

\&lt;xs:element name=&quot;PdfTemplate&quot; type=&quot;css:PdfTemplateType&quot;/\&gt;

\&lt;xs:complexType name=&quot;PdfTemplateType&quot;\&gt;

\&lt;xs:sequence\&gt;

\&lt;xs:element name=&quot;PdfDocument&quot; maxOccurs=&quot;unbounded&quot;\&gt;

\&lt;xs:complexType\&gt;

\&lt;xs:sequence\&gt;

\&lt;xs:element name=&quot;SignatureField&quot; type=&quot;css:PdfSignatureInfoType&quot; maxOccurs=&quot;unbounded&quot;/\&gt;

\&lt;/xs:sequence\&gt;

\&lt;xs:attribute name=&quot;title&quot; type=&quot;xs:string&quot; use=&quot;optional&quot;/\&gt;

\&lt;/xs:complexType\&gt;

\&lt;/xs:element\&gt;

\&lt;/xs:sequence\&gt;

\&lt;/xs:complexType\&gt;

\&lt;xs:complexType name=&quot;PdfSignatureInfoType&quot;\&gt;

\&lt;xs:all\&gt;

\&lt;xs:element name=&quot;PdfAttributes&quot; type=&quot;css:PdfAttributesType&quot;/\&gt;

\&lt;xs:element name=&quot;Appearance&quot; type=&quot;css:AppearanceType&quot; minOccurs=&quot;0&quot;/\&gt;

\&lt;/xs:all\&gt;

\&lt;xs:attribute name=&quot;name&quot; type=&quot;xs:string&quot; use=&quot;optional&quot;/\&gt;

\&lt;xs:attribute name=&quot;order&quot; type=&quot;xs:integer&quot; use=&quot;optional&quot;/\&gt;

\&lt;/xs:complexType\&gt;

\&lt;css:PdfTemplate\&gt; és l&#39;element arrel de qualsevol plantilla de signatura PDF. Aquest element consisteix en una seqüència d&#39;elements \&lt;css:PdfDocument\&gt;, cadascun dels quals defineix una variació de la plantilla (és a dir, plantilles diferents en la pràctica). D&#39;aquesta manera, quan s&#39;hagi de signar un document PDF, fent ús d&#39;una plantilla determinada, s&#39;utilitzarà la &quot;variant&quot; que contingui l&#39;element /css:PdfTemplate/css:PdfDocument, l&#39;atribut /css:PdfTemplate/css:PdfDocument/@title del qual coincideixi amb el títol del document PDF. És a dir, amb el valor que estigui associat a la clau Title del diccionari d&#39;informació del document. Cal tenir en compte que sempre hi hauran correspondències (matching) entre un document PDF i un element /css:PdfTemplate/css:PdfDocument que manqui de l&#39;atribut title.

Per un altre costat, en aquells casos en que:

- El títol del document PDF no coincideixi amb l&#39;atribut title de cap dels elements /css:PdfTemplate/css:PdfDocument de la plantilla.
- I, a més, no hi hagi cap element /css:PdfTemplate /css:PdfDocument que no tingui l&#39;atribut title.

Aleshores, s&#39;haurà d&#39;utilitzar la plantilla de signatures PDF per defecte, és a dir, la plantilla urn:Safelayer:TWS:policies:common:templates:pdf:default. Aquesta plantilla es descriu més endavant en Plantilla de signatures PDF per defecte.

- Cada element \&lt;css:PdfDocument\&gt; conté un nombre il·limitat d&#39;elements \&lt;css:SignatureField\&gt;, cadascun dels quals descriu els atributs i l&#39;aparença d&#39;un camp de signatura del document PDF.
- Cada element \&lt;css:SignatureField\&gt; conté els següents elements:

- \&lt;css:PdfAttributes\&gt;, Que determina les característiques de la signatura. Vegi Element \&lt;css:PdfAttributes\&gt; per obtenir més detalls sobre aquest element.

- \&lt;css:Appearance\&gt;, Que determina l&#39;aparença &quot;visual&quot; de la signatura. Vegi Element \&lt;css:Appearance\&gt; per a més detalls sobre aquest element. Si aquest element s&#39;omet, la signatura que es generi serà invisible.

- I els següents atributs:

- //SignatureField/@name, que identifica (pel seu nom) el camp de signatura del document PDF a què es refereixen els atributs i l&#39;aparença que defineix aquest element.

- //SignatureField/@order, que identifica (pel seu nombre d&#39;ordre) el camp de signatura del document PDF a què es refereixen els atributs i l&#39;aparença que defineix aquest element, tenint en compte que el valor 0 identifica el &quot;següent&quot; camp de signatura (sigui quin sigui el seu número d&#39;ordre).

L&#39;element /css:PdfTemplate/css:PdfDocument/css:SignatureField que s&#39;utilitzarà per establir els atributs i l&#39;aparença de la signatura PDF es determinarà de la manera següent:

a) Si en la petició s&#39;ha especificat el nom del camp de signatura (element //DSS:OptionalInputs/css:StoreSignatureField) aleshores s&#39;utilitzarà l&#39;element /css:PdfTemplate/css:PdfDocument/css:SignatureField l&#39;atribut //SignatureField/@name del qual contingui el mateix valor.

b) Si l&#39;atribut //SignatureField/@name no és present, la petició no conté l&#39;element //DSS:OptionalInputs/css:StoreSignatureField, o bé no hi ha coincidència entre un i altre, llavors s&#39;ha d&#39;utilitzar l&#39;element /css:PdfTemplate/css:PdfDocument/css:SignatureField l&#39;atribut //SignatureField/@order del qual sigui 0 o coincideixi amb el resultat d&#39;incrementar (en un) el nombre de camps de signatura que contingui el document PDF.

c) Si no s&#39;ha pogut seleccionar cap element /css:PdfTemplate/css:PdfDocument/css:SignatureField en base als criteris anteriors, llavors cal utilitzar el (únic) camp /css:PdfTemplate/css:PdfDocument/css:SignatureField de la plantilla per defecte del sistema (és a dir, la plantilla urn:Safelayer:TWS:policies:common:templates:pdf:default). Aquesta plantilla es descriu seguidament.

**Plantilla de signatures PDF per defecte**

TrustedX conté una plantilla per defecte per realitzar signatures PDF, que s&#39;identifica per urn:Safelayer:TWS:policies:common:templates:pdf:default i que té la següent definició:

\&lt;css:PdfTemplate xmlns:css=&quot;http://www.safelayer.com/TWS&quot;\&gt;

\&lt;css:PdfDocument\&gt;

\&lt;css:SignatureField\&gt;

\&lt;css:PdfAttributes\&gt;

\&lt;css:signatureAlg\&gt;DETACHED\&lt;/css:signatureAlg\&gt;

\&lt;css:validationMethod\&gt;PPKMS\&lt;/css:validationMethod\&gt;

\&lt;css:signaturePosition\&gt;LAST\&lt;/css:signaturePosition\&gt;

\&lt;/css:PdfAttributes\&gt;

\&lt;/css:SignatureField\&gt;

\&lt;/css:PdfDocument\&gt;

\&lt;/css:PdfTemplate\&gt;

On es pot observar que, quan es genera una signatura en un document PDF, utilitzant la plantilla per defecte de TrustedX, aquesta signatura tindrà les següents característiques:

- Serà invisible i s&#39;ubicarà a l&#39;última pàgina.
- El seu format serà el d&#39;una signatura PKCS#7 de tipus detached. És a dir, s&#39;ha d&#39;associar el valor adbe.pkcs.detached a la clau _SubFilter_ del diccionari de la signatura.
- El signature-handler que, de manera preferent, s&#39;ha d&#39;utilitzar per a verificar la signatura és el de Microsoft. És a dir, s&#39;ha d&#39;associar el valor Adobe.PPKMS a la clau Filter del diccionari de la signatura.

**Exemple de plantilla de signatures PDF**

El següent codi XML és un exemple de plantilla de signatures PDF:

\&lt;?xml version=&quot;1.0&quot; encoding=&quot;UTF-8&quot;?\&gt;

\&lt;css:PdfTemplate xmlns:css=&quot;http://www.safelayer.com/TWS&quot; xmlns:xsi=&quot;http://www.w3.org/2001/XMLSchema-instance&quot;\&gt;

\&lt;css:PdfDocument title=&quot;Document1&quot;\&gt;

\&lt;css:SignatureField name=&quot;Signature1&quot;\&gt;

\&lt;css:PdfAttributes\&gt;

\&lt;css:signatureAlg\&gt;SHA1\&lt;/css:signatureAlg\&gt;

\&lt;css:validationMethod\&gt;PPKMS\&lt;/css:validationMethod\&gt;

\&lt;css:signaturePosition\&gt;ADDLAST\&lt;/css:signaturePosition\&gt;

\&lt;css:params\&gt;

\&lt;css:location\&gt;Barcelona\&lt;/css:location\&gt;

\&lt;css:reason\&gt;Author\&lt;/css:reason\&gt;

\&lt;css:contactInfo\&gt;+345818090\&lt;/css:contactInfo\&gt;

\&lt;/css:params\&gt;

\&lt;/css:PdfAttributes\&gt;

\&lt;/css:SignatureField\&gt;

\&lt;css:SignatureField order=&quot;0&quot;\&gt;

\&lt;css:PdfAttributes\&gt;

\&lt;css:signatureAlg\&gt;SHA1\&lt;/css:signatureAlg\&gt;

\&lt;css:validationMethod\&gt;PPKMS\&lt;/css:validationMethod\&gt;

\&lt;css:signaturePosition\&gt;ADDLAST\&lt;/css:signaturePosition\&gt;

\&lt;css:params\&gt;

\&lt;css:location\&gt;Barcelona\&lt;/css:location\&gt;

\&lt;css:reason\&gt;Author\&lt;/css:reason\&gt;

\&lt;css:contactInfo\&gt;+345818090\&lt;/css:contactInfo\&gt;

\&lt;/css:params\&gt;

\&lt;/css:PdfAttributes\&gt;

\&lt;css:Appearance\&gt;

\&lt;css:Rect x0=&quot;31&quot; y0=&quot;200&quot; x1=&quot;557&quot; y1=&quot;40&quot;/\&gt;

\&lt;css:Background\&gt;

\&lt;css:image encodeType=&quot;base64&quot;\&gt;

\&lt;css:data\&gt;/9j/4...Q==\&lt;/css:data\&gt;

\&lt;css:imageSize width=&quot;400&quot; height=&quot;40&quot;/\&gt;

\&lt;css:position x=&quot;50&quot; y=&quot;35&quot;/\&gt;

\&lt;/css:image\&gt;

\&lt;/css:Background\&gt;

\&lt;css:Foreground\&gt;

\&lt;css:image encodeType=&quot;base64&quot;\&gt;

\&lt;css:data\&gt;/9j/...ZCg==\&lt;/css:data\&gt;

\&lt;css:imageSize width=&quot;80&quot; height=&quot;30&quot;/\&gt;

\&lt;css:position x=&quot;223&quot; y=&quot;1&quot;/\&gt;

\&lt;/css:image\&gt;

\&lt;css:text\&gt;

\&lt;css:properties color=&quot;0 0 0&quot; fontSize=&quot;5&quot;/\&gt;

\&lt;css:position x=&quot;150&quot; y=&quot;35&quot;/\&gt;

\&lt;css:SignatureInfos\&gt;

\&lt;css:signatureInfo title=&quot;Autor de la firma: &quot; id=&quot;Subject&quot;/\&gt;

\&lt;css:signatureInfo title=&quot;Emisor del certificado: &quot; id=&quot;Issuer&quot;/\&gt;

\&lt;css:signatureInfo title=&quot;Número de serie: &quot; id=&quot;SerialNumber&quot;/\&gt;

\&lt;css:signatureInfo title=&quot;Razón: &quot; id=&quot;Reason&quot;/\&gt;

\&lt;css:signatureInfo title=&quot;Localitzación: &quot; id=&quot;Location&quot;/\&gt;

\&lt;css:signatureInfo title=&quot;Información de contacto: &quot; id=&quot;ContactInfo&quot;/\&gt;

\&lt;css:signatureInfo title=&quot;Fecha de firma: &quot; id=&quot;Date&quot;/\&gt;

\&lt;/css:SignatureInfos\&gt;

\&lt;/css:text\&gt;

\&lt;/css:Foreground\&gt;

\&lt;/css:Appearance\&gt;

\&lt;/css:SignatureField\&gt;

\&lt;/css:PdfDocument\&gt;

\&lt;css:PdfDocument\&gt;

\&lt;css:SignatureField order=&quot;0&quot;\&gt;

\&lt;css:PdfAttributes\&gt;

\&lt;css:signatureAlg\&gt;SHA1\&lt;/css:signatureAlg\&gt;

\&lt;css:validationMethod\&gt;PPKMS\&lt;/css:validationMethod\&gt;

\&lt;css:signaturePosition\&gt;LAST\&lt;/css:signaturePosition\&gt;

\&lt;/css:PdfAttributes\&gt;

\&lt;/css:SignatureField\&gt;

\&lt;/css:PdfDocument\&gt;

\&lt;/css:PdfTemplate\&gt;

# 5Gestió de dades de volum gran

Si els documents XML inclouen elements amb valors de volum gran, Axis experimenta problemes de rendiment. Per pal·liar aquests problemes, podem guardar en arxiu aquests valors, deixant a l&#39;XML una referència a aquest arxiu. D&#39;aquesta manera, el tamany de l&#39;XML que gestiona Axis es redueix considerablement. Més endavant, en la capa de transport, es substitueixen les referències per les dades guardades en arxiu.

Per defecte, les dades no es tracten com a arxiu.

## 5.1Gestió de peticions amb dades de gran tamany

Quan el document a signar tingui un volum considerable, i cal enviar-lo sencer en la petició de signatura, podem experimentar problemes de rendiment d&#39;Axis.

La classe SmartSignRequest ofereix certs mètodes que permeten gestionar com a arxius les dades de gran volum.

Mètodes:

- setInputBase64Data(fileName, format): Per documents binaris.
- setInputXmlBase64(fileName, format): Per documents XML.
- setInputPdfBase64Data(fileName, format): Per documents PDF.

On:

fileName és el nom del fitxer que conté les dades a signar

format és el format de les guardades en arxiu, i que pot prendre els següents valors:

- Constants.SourceFormat.BASE64

- Constants.SourceFormat.RAW

La classe SmartSignRequest també ofereix certs mètodes que permeten que en la resposta les dades de gran volum puguin tractar-se també com a arxius:

- enableSignatureBase64(format): Per signatures binàries.
- enableSignatureXmlBase64(format): Per signatures XML.
- enableDocumentWithSignaturePdf(format): Per documents PDF signats.
- enableDocumentWithSignatureXmlBase64(format): Per signatures XML enveloped.

On:

format és el format de les guardades en arxiu, i que pot prendre els següents valors:

- Constants.SourceFormat.BASE64

- Constants.SourceFormat.RAW

Els següents mètodes deshabilitarien l&#39;habilitat amb els corresponents mètodes anteriors:

- disableSignatureBase64(format): Per signatures binàries.
- disableSignatureXmlBase64(format): Per signatures XML.
- disableDocumentWithSignaturePdf(format): Per documents PDF signats.
- disableDocumentWithSignatureXmlBase64(format): Per signatures XML enveloped.

En fer un _disable_ després d&#39;un _enable_, deshabilitarem el tractament com a arxiu de les dades corresponents. Recordem que per defecte el tractament com a arxiu està deshabilitat.

**NOTA 1** : En cas de que habilitem la gestió de dades de la resposta en fitxer, aquests es guardaran al directori indicat al paràmetre Response.savePath de la configuració de l&#39;SmartWrapper. Si aquest paràmetre no és present, els arxius es guardaran al directori d&#39;execució.

**NOTA 2** : Si volem que les dades d&#39;entrada s&#39;agafin directament d&#39;un directori base concret, cal indicar el paràmetre Request.loadPath a la configuració d&#39;SmartWrapper. Si no s&#39;especifica, el directori base serà el d&#39;execució.

## 5.2Gestió de respostes amb dades de gran tamany

Si s&#39;ha habilitat en la petició de signatura el tractament com a fitxers de dades de la resposta, en cas de voler recuperar aquestes dades per codi, haurem de fer-ho mitjançant els mètodes que veurem a continuació.

La classe SmartSignResponse ofereix doncs mètodes que permeten obtenir les dades de la resposta quan aquestes s&#39;han gestionat com a arxius. En aquest cas es tractarà de signatures o documents signats.

Mètodes:

- getDocumentWithSignaturePdf(): Per obtenir la referència a un document PDF signat.
- getDocumentWithSignatureXml(): Per obtenir la referència a un document que conté la referència a una signatura XML enveloped.
- getSignatureBase64(): Per obtenir la referència a una signatura binària.
- getSignatureXml(): Per obtenir la referència a una signatura XML.

Quan parlem de referència volem dir el nom del fitxer al directori de sortida.

A partir de els referències obtingudes amb els mètodes anteriors, podem recuperar per codi el contingut dels fitxers que contenen les dades de la resposta:

- getReferenceFileContent(String reference, boolean deleteFile)

On:

- reference és el nom del fitxer.
- deleteFile és un booleà amb el qual podem esborrar el document guardat en fitxer:

- true: L&#39;arxiu que conté el valor, s&#39;esborrarà després de llegir el seu contingut

- false: L&#39;arxiu no s&#39;esborrarà.

## 5.3Exemple de gestió en arxius per generació d&#39;una signatura XAdES-BES enveloping

import org.apache.axis.encoding.Base64;

import org.apache.axis.message.SOAPHeaderElement;

import org.apache.commons.configuration.Configuration;

import utils.\*;

import com.safelayer.trustedx.client.smartwrapper.\*;

public class CreateSignature\_XAdES\_BES\_Enveloped\_BigFile {

private static final String path\_in = &quot;in/docs\_to\_sign/BigFiles/&quot;;

private static final String path\_out = &quot;out/Signatures/BigFiles/&quot;;

private static final String filename = &quot;Demo-BigFile.xml&quot;;

public static void main(String[] args) {

try {

Configuration conf = TrustedXConfiguration.getConfiguration();

String host = conf.getString(&quot;host&quot;);

String distinguishedName = conf.getString(&quot;distinguishedname&quot;);

String dipositari = conf.getString(&quot;dipositari&quot;);

String rol = conf.getString(&quot;rol&quot;);

// Definition of Signature Request endpoint

SmartSignRequest ssr = new SmartSignRequest(host);

// Add customized header elements for SOAP

Stub stub = (Stub) ssr.getStub();

stub.setHeader(null, &quot;Rol&quot;, rol);

stub.setHeader(null, &quot;Dipositari&quot;, dipositari);

// XML Signature (XAdES)

ssr.setProfile(Constants.Profile.XADES);

// Referència al fitxer que conté les dades a signar

// Paràmetres: path (codificat en Base64) del fitxer + tipus de dades del fitxer (Raw o Base64)

ssr.setInputXmlBase64File(Base64.encode((path\_in + filename).getBytes()), Constants.SourceFormat.RAW);

// Habilitem la gestió en arxiu de la signatura en la resposta

ssr.enableDocumentWithSignatureXmlBase64File(Constants.SourceFormat.RAW);

// XAdES signature form

ssr.setSignatureFormat(Constants.SignatureFormat.BES);

// Signature Placement

ssr.setSignaturePlacement(Constants.SignaturePlacement.ENVELOPED);

ssr.setXmlEnvelopedXPathAfter(&quot;//\*[local-name()=&#39;ssc&#39;]//\*[local-name()=&#39;description&#39;]&quot;);

// Key selection using Distinguished Name

ssr.setKeySubjectName(distinguishedName);

// Sending request

SmartSignResponse ssrs = ssr.send();

// Retrieveing signature

if (UtilTrustedX.checkSW(ssrs.getResultMajor(), ssrs.getResultMinor(), ssrs.getResultMessage())) {

String destFilename = path\_out + filename.substring(0, filename.lastIndexOf(&quot;.&quot;))

+ &quot;\_Signature\_XAdES\_BES\_Enveloped.xml&quot;;

Util.writeBinaryFile(destFilename, ssrs.getDocumentWithSignatureXml().getBytes());

}

} catch (Exception e) {

e.printStackTrace();

}

}

}

# 6Exemple d&#39;ús amb SoapUI

A l&#39;apartat de Documentació de Integració d&#39;aquest servei es disposa d&#39;uns exemples de SOAPUI amb un certificat en format pkcs#12 (pin : 1234) per realitzar l&#39;autenticació al servei.

SoapUI és una eina per a realitzar proves d&#39;APIs del tipus SOAP o REST. Es pot descarregar gratuïtament a la web [https://www.soapui.org/](https://www.soapui.org/). Aquest breu guía ha sigut creada amb la versió SoapUI 5.3.0.

## 6.1Importar un projecte

Obrir SoapUI i utilitzar l&#39;opció _Import_ situada al menú de la part superior.

![](RackMultipart20220630-1-6kytqz_html_73640d09d571aa40.png)

Seleccionar el projecte proporcionat a la web. L&#39;eina crearà una estructura semblant a la seguent:

![](RackMultipart20220630-1-6kytqz_html_ce3ad80d34ba4855.png)

Els missatges SOAP disponibles són:

- Signatura amb ROL i autenticació amb certificat
- Signatura sense ROL i amb autenticació amb certificat

## 6.2Afegir certificat PKCS#12

Per utilitzar un certificat personal per autenticar amb el servei de signatura, prémer el botó _Preferences_ situat al menú superior de l&#39;eina.

![](RackMultipart20220630-1-6kytqz_html_8f8931a27cea9830.png)

A l&#39;apartat _SSL Setting_ seleccionar el certificate PKCS#12 proporcionat i posar la contrasenya tal com s&#39;indica a la següent figura:

![](RackMultipart20220630-1-6kytqz_html_bbdf99203a933d9a.png)
