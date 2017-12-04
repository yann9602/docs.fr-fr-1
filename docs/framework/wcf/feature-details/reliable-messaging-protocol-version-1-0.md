---
title: "Protocole de messagerie fiable version 1.0"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a5509a5c-de24-4bc2-9a48-19138055dcce
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5657b48a648603f24e89c0eebd1285ed9a505e54
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="reliable-messaging-protocol-version-10"></a>Protocole de messagerie fiable version 1.0
Cette rubrique traite des détails de l'implémentation [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] pour le protocole WS-Reliable Messaging de février 2005 (version 1.0) nécessaire pour l'interopérabilité à l'aide du transport HTTP. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] suit la spécification WS-Reliable Messaging avec les contraintes et les éclaircissements présentés dans cette rubrique. Notez que le protocole WS-ReliableMessaging version 1.0 est implémenté à partir de [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)].  
  
 Le protocole de messagerie WS-Reliable de février 2005 est implémenté dans [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] par <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>.  
  
 Pour plus de simplicité, la rubrique utilise les rôles suivants :  
  
-   Initiateur : client qui initialise la création de la séquence de message WS-Reliable.  
  
-   Répondeur : service qui reçoit les demandes de l'initiateur.  
  
 Ce document utilise les préfixes et les espaces de noms répertoriés dans le tableau suivant.  
  
|Préfixe|Espace de noms|  
|------------|---------------|  
|wsrm|http://schemas.xmlsoap.org/ws/2005/02/rm|  
|netrm|http://schemas.microsoft.com/ws/2006/05/rm|  
|s|http://www.w3.org/2003/05/soap-envelope|  
|wsa|http://schemas.xmlsoap.org/ws/2005/08/addressing|  
|wsse|http://docs.oasis-open.org/wss/2004/01/oasis-200401-wssecurity-secext-1.0.xsd|  
  
## <a name="messaging"></a>Messagerie  
  
### <a name="sequence-establishment-messages"></a>Messages d'établissement de séquence  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] implémente des messages `CreateSequence` et `CreateSequenceResponse` pour établir une séquence de message fiable. Les contraintes suivantes s'appliquent :  
  
-   B1101 : l'initiateur [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ne génère pas l'élément Expires facultatif dans le message `CreateSequence` ou, lorsque le message `CreateSequence` contient un élément `Offer`, l'élément `Expires` facultatif dans l'élément `Offer`.  
  
-   B1102 : lors de l'accès au message `CreateSequence`, le [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]`Responder` envoie et reçoit les deux éléments `Expires` s'ils existent, mais n'utilise pas leurs valeurs.  
  
 La messagerie WS-Reliable introduit le mécanisme `Offer` pour établir deux séquences corrélées réciproques qui forment une session.  
  
-   R1103 : si `CreateSequence` contient un élément `Offer`, le répondeur de messagerie fiable doit soit accepter la séquence et répondre avec `CreateSequenceResponse` contenant un élément `wsrm:Accept`, formant deux séquences réciproques corrélées, soit rejeter la demande `CreateSequence`.  
  
-   R1104 : l'`SequenceAcknowledgement` et les messages d'application qui passent sur la séquence réciproque doivent être envoyés à la référence de point de terminaison `ReplyTo` de `CreateSequence`.  
  
-   R1105 : les références de point de terminaison `AcksTo` et `ReplyTo` dans `CreateSequence` doivent avoir des valeurs d'adresse qui correspondent au niveau des octets.  
  
     Le répondeur [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] vérifie que la partie URI des ERP `AcksTo` et `ReplyTo` est identique avant de créer une séquence.  
  
-   R1106 : les références de point de terminaison `AcksTo` et `ReplyTo` dans `CreateSequence` doivent avoir le même jeu de paramètres de référence.  
  
     [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] n'applique pas, mais présuppose que les [paramètres de référence] de `AcksTo` et `ReplyTo` sur `CreateSequence` sont identiques et utilise les [paramètres de référence] de la référence de point de terminaison `ReplyTo` pour les accusés de réception et les messages de séquence réciproque.  
  
-   R1107 : lorsque deux séquences réciproques sont établies à l'aide du mécanisme `Offer`, l'`SequenceAcknowledgement` et les messages d'application qui traversent les séquences réciproques doivent être envoyés à la référence de point de terminaison `ReplyTo` de `CreateSequence`.  
  
-   R1108 : lorsque deux séquences réciproques sont établies à l'aide du mécanisme Offer, la propriété `[address]` de l'élément enfant `wsrm:AcksTo` de la référence de point de terminaison de l'élément `wsrm:Accept` de la `CreateSequenceResponse` doit correspondre octet par octet à l'URI de destination de `CreateSequence`.  
  
-   R1109 : lorsque deux séquences réciproques sont établies à l'aide du mécanisme `Offer`, les messages envoyés par l'initiateur et les accusés de réception des messages envoyés par le répondeur doivent être envoyés à la même référence de point de terminaison.  
  
     [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] utilise la messagerie WS-Reliable pour établir des sessions fiables entre l'initiateur et le répondeur. L'implémentation de la messagerie WS-Reliable [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] fournit une session fiable pour les modèles de messagerie en duplex intégral, de demande-réponse et unidirectionnels. La messagerie WS-Reliable `Offer` mécanisme sur `CreateSequence` / `CreateSequenceResponse` vous permet d’établir deux séquences réciproques corrélées et fournit un protocole de session qui convient à tous les points de terminaison de message. Comme [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] fournit une garantie de sécurité pour ce type de session incluant la protection de bout en bout de l'intégrité de la session, il est pratique de s'assurer que les messages destinés au même correspondant arrivent à la même destination. Cela permet également la superposition des accusés de réception de séquence sur les messages d'application. Par conséquent, les contraintes R1104, R1105 et R1108 s'appliquent à [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
 Exemple de message `CreateSequence`.  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <a:Action s:mustUnderstand="1">  
      http://schemas.xmlsoap.org/ws/2005/02/rm/CreateSequence  
    </a:Action>  
    <a:ReplyTo>  
      <a:Address>          
         http://Business456.com/clientA        
      </a:Address>  
    </a:ReplyTo>  
    <a:MessageID>  
      urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36  
    </a:MessageID>  
    <a:To s:mustUnderstand="1">  
      http://Business456.com/clientA  
    </a:To>  
  </s:Header>  
  <s:Body>  
    <wsrm:CreateSequence>  
      <wsrm:AcksTo>  
       <wsa:Address>  
         http://Business456.com/clientA  
       </wsa:Address>  
     </wsrm:AcksTo>  
     <wsrm:Offer>  
      <wsrm:Identifier>  
        urn:uuid:0afb8d36-bf26-4776-b8cf-8c91fddb5496  
      </wsrm:Identifier>  
     </wsrm:Offer>  
   </wsrm:CreateSequence>  
  </s:Body>  
</s:Envelope>  
```  
  
 Exemple de message `CreateSequenceResponse`.  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <a:Action s:mustUnderstand="1">  
      http://schemas.xmlsoap.org/ws/2005/02/rm/CreateSequenceResponse  
    </a:Action>  
    <a:RelatesTo>  
      urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36  
    </a:RelatesTo>  
    <a:To s:mustUnderstand="1">  
      http://Business456.com/clientA  
    </a:To>  
  </s:Header>  
  <s:Body>  
   <wsrm:CreateSequenceResponse>  
    <Identifier>  
     urn:uuid:eea0a36c-b38a-43e8-8c76-2fabe2d76386  
    </Identifier>  
    <Accept>  
    <AcksTo>  
      <a:Address>  
        http://BusinessABC.com/serviceA  
      </a:Address>  
    </AcksTo>  
    </Accept>  
   </wsrm:CreateSequenceResponse>  
  </s:Body>  
</s:Envelope>  
```  
  
### <a name="sequence"></a>Séquence  
 Voici une liste des contraintes qui s'appliquent aux séquences :  
  
-   B1201 :[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] génère et accède à des numéros de séquence ne dépassant pas `xs:long`de valeur inclusive maximale, 9223372036854775807.  
  
-   B1202 :[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] génère toujours un vide dernier message avec l’URI d’action de http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage.  
  
-   B1203 : [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] reçoit et remet un message avec un en-tête Sequence qui contient un élément `LastMessage` tant que l'URI action n'est pas http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage.  
  
 Exemple d'en-tête Sequence.  
  
```xml  
<wsrm:Sequence>  
  <wsrm:Identifier>  
    urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36  
  </wsrm:Identifier>  
  <wsrm:MessageNumber>  
    10  
  </wsrm:MessageNumber>  
  <wsrm:LastMessage/>  
 </wsrm:Sequence>  
```  
  
### <a name="ackrequested-header"></a>En-tête AckRequested  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] utilise l'en-tête `AckRequested` comme un mécanisme persistant. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ne génère pas l'élément facultatif `MessageNumber`. À la réception d'un message avec un en-tête `AckRequested` contenant l'élément `MessageNumber`, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ignore la valeur de l'élément `MessageNumber`, comme indiqué dans l'exemple suivant.  
  
```xml  
<wsrm:AckRequested>  
  <wsrm:Identifier>  
    urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36  
  </wsrm:Identifier>  
</wsrm:AckRequested>  
```  
  
### <a name="sequenceacknowledgement-header"></a>En-tête SequenceAcknowledgement  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] utilise un mécanisme de superposition pour les accusés de réception de séquence fournis dans la messagerie WS-Reliable.  
  
-   R1401 : lorsque deux séquences réciproques sont établies à l'aide du mécanisme `Offer`, l'en-tête `SequenceAcknowledgement` peut être inclus dans tout message d'application transmis au destinataire souhaité.  
  
-   B1402 : lorsque [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] doit générer un accusé de réception avant de recevoir un message de séquence (par exemple, pour satisfaire un message `AckRequested`), [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] génère un en-tête `SequenceAcknowledgement` qui contient la plage 0-0, comme indiqué dans l'exemple suivant.  
  
    ```xml  
    <wsrm:SequenceAcknowledgement>  
      <wsrm:Identifier>  
        urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36  
      </wsrm:Identifier>  
      <wsrm:AcknowledgementRange Upper="0" Lower="0"/>  
    </wsrm:SequenceAcknowledgement>  
    ```  
  
-   B1403 : [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ne génère pas d'en-têtes `SequenceAcknowledgement` contenant un élément `Nack` mais prend en charge les éléments `Nack`.  
  
### <a name="ws-reliablemessaging-faults"></a>Erreurs de la messagerie WS-Reliable  
 Voici une liste des contraintes qui s'appliquent à l'implémentation [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] des erreurs de messagerie WS-Reliable.  
  
-   B1501 : [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ne génère pas d'erreurs `MessageNumberRollover`.  
  
-   B1502 :[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] peut générer un point de terminaison `CreateSequenceRefused` comme décrit dans la spécification des erreurs.  
  
-   B1503:when le point de terminaison de service atteint sa limite de connexions et ne peut pas traiter de nouvelles connexions, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] génère un autre `CreateSequenceRefused` sous-code, d’erreur `netrm:ConnectionLimitReached`, comme illustré dans l’exemple suivant.  
  
    ```xml  
    <s:Envelope>  
      <s:Header>  
        <wsa:Action>  
          http://schemas.xmlsoap.org/ws/2005/08/addressing/fault  
        </wsa:Action>  
      </s:Header>  
      <s:Body>  
        <s:Fault>  
          <s:Code>  
            <s:Value>  
              s:Receiver  
            </s:Value>  
            <s:Subcode>  
              <s:Value>  
                wsrm:CreateSequenceRefused  
              </s:Value>  
              <s:Subcode>  
                <s:Value>  
                  netrm:ConnectionLimitReached  
                </s:Value>  
              </s:Subcode>  
            </s:Subcode>  
          </s:Code>  
          <s:Reason>  
            <s:Text xml:lang="en">  
              [Reason]  
            </s:Text>  
          </s:Reason>  
        </s:Fault>  
      </s:Body>  
    </s:Envelope>  
    ```  
  
### <a name="ws-addressing-faults"></a>Erreurs WS-Addressing  
 Puisque la messagerie WS-Reliable utilise WS-Addressing, son implémentation [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] peut générer des erreurs WS-Addressing. Cette section traite des erreurs WS-Addressing que [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] génère explicitement au niveau de la couche de la messagerie WS-Reliable :  
  
-   B1601 :[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] génère l’erreur d’en-tête de Message Addressing requis lorsque l’une des valeurs suivantes est vraie :  
  
    -   Un message n'a pas d'en-tête `Sequence` ni d'en-tête `Action`.  
  
    -   Un message `CreateSequence` n'a pas d'en-tête `MessageId`.  
  
    -   Un message `CreateSequence` n'a pas d'en-tête `ReplyTo`.  
  
-   B1602 :[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] génère l’erreur pas pris en charge par Action en réponse à un message qui est manquant, un `Sequence` en-tête et a une `Action` en-tête n’est pas reconnu dans la spécification WS-Reliable Messaging.  
  
-   B1603 :[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] génère l’erreur de point de terminaison non disponible pour indiquer que le point de terminaison ne traite pas la séquence suite basée l’examen de la `CreateSequence` en-têtes d’adressage du message.  
  
## <a name="protocol-composition"></a>Composition du protocole  
  
### <a name="composition-with-ws-addressing"></a>Composition avec WS-Addressing  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] prend en charge deux versions de WS-Addressing : WS-Addressing 2004/08 [WS-ADDR] et W3C WS-Addressing 1.0 Recommendations [WS-ADDR-CORE] et [WS-ADDR-SOAP]  
  
 Bien que la spécification de la messagerie WS-Reliable mentionne WS-Addressing 2004/08 uniquement, cela ne constitue pas une restriction en ce qui concerne la version WS-Addressing à utiliser. Voici une liste des contraintes qui s'appliquent à [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] :  
  
-   R2101 : les deux WS-Addressing 2004/08 et WS-Addressing 1.0 peuvent être utilisé avec la messagerie WS-Reliable.  
  
-   R2102:A une seule version de WS-Addressing doit être utilisée dans une séquence WS-Reliable Messaging donnée ou une paire de séquences réciproques corrélées à l’aide de la `wsrm:Offer` mécanisme.  
  
### <a name="composition-with-soap"></a>Composition avec SOAP  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] prend en charge l'utilisation de SOAP 1.1 et de SOAP 1.2 avec la messagerie WS-Reliable.  
  
### <a name="composition-with-ws-security-and-ws-secureconversation"></a>Composition avec WS-Security et WS-SecureConversation  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] fournit une protection pour les séquences de messagerie WS-Reliable en utilisant le transport sécurisé (HTTPS), la composition avec WS-Security et la composition avec WS-Secure Conversation. Voici une liste des contraintes qui s'appliquent à [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] :  
  
-   R2301 : pour protéger l’intégrité d’une séquence WS-ReliableMessaging en plus de l’intégrité et la confidentialité des messages individuels, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] nécessite que WS-Secure Conversation doit être utilisée.  
  
-   R2302:AWS-session de Secure Conversation doit être établie avant d’établir des séquences de messagerie WS-Reliable.  
  
-   R2303 : si la durée de vie de la séquence de messagerie WS-Reliable dépasse celle de la session WS-Secure Conversation, le `SecurityContextToken` établi à l'aide de WS-Secure Conversation doit être renouvelé par le biais de la liaison WS-Secure Conversation Renewal correspondante.  
  
-   B2304:ws-séquence de messagerie fiable ou une paire de séquences réciproques corrélées sont toujours liées à une seule session WS-SecureConversation.  
  
     La source [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] génère l'élément `wsse:SecurityTokenReference` dans la section d'extensibilité d'élément du message `CreateSequence`.  
  
-   R2305:when composé avec WS-Secure Conversation, un `CreateSequence` message doit contenir la `wsse:SecurityTokenReference` élément.  
  
## <a name="ws-reliable-messaging-ws-policy-assertion"></a>Assertion WS-Policy de la messagerie WS-Reliable  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] utilise l'assertion WS-Policy de la messagerie WS-Reliable `wsrm:RMAssertion` pour décrire des fonctions de points de terminaison. Voici une liste des contraintes qui s'appliquent à [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] :  
  
-   B3001 : [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] attache l'assertion WS-Policy `wsrm:RMAssertion` aux éléments `wsdl:binding`. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] prend en charge des pièces jointes aux éléments `wsdl:binding` et `wsdl:port`.  
  
-   B3002 : [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] prend en charge les propriétés facultatives suivantes de l'assertion de messagerie WS-Reliable et assure leur contrôle sur l'[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] de `ReliableMessagingBindingElement` :  
  
    -   `wsrm:InactivityTimeout`  
  
    -   `wsrm:AcknowledgementInterval`  
  
     Voici un exemple.  
  
    ```xml  
    <wsrm:RMAssertion>  
      <wsrm:InactivityTimeout Milliseconds="600000" />  
      <wsrm:AcknowledgementInterval Milliseconds="200" />  
    </wsrm:RMAssertion>  
    ```  
  
## <a name="flow-control-ws-reliable-messaging-extension"></a>Extension de messagerie WS-Reliable pour le contrôle de flux  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] utilise l'extensibilité de la messagerie WS-Reliable pour renforcer le contrôle facultatif sur le flux des messages de séquence.  
  
 Contrôle de flux est activé en définissant le `ReliableSessionBindingElement`de `FlowControlEnabled``bool` propriété `true`. Voici une liste des contraintes qui s'appliquent à [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] :  
  
-   B4001 : lorsque le contrôle du flux de la messagerie fiable est activé, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] génère un élément `netrm:BufferRemaining` dans l'extensibilité d'élément de l'en-tête `SequenceAcknowledgement`.  
  
-   B4002 : lorsque le contrôle du flux de la messagerie fiable est activé, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ne requiert pas qu'un élément `netrm:BufferRemaining` soit présent dans l'en-tête `SequenceAcknowledgement`, comme indiqué dans l'exemple suivant.  
  
    ```xml  
    <wsrm:SequenceAcknowledgement>  
      <wsrm:Identifier>  
        http://fabrikam123.com/abc  
      </wsrm:Identifier>  
      <wsrm:AcknowledgementRange Upper="1" Lower="1"/>             
      <netrm:BufferRemaining>  
        8  
      </netrm:BufferRemaining>  
    </wsrm:SequenceAcknowledgement>  
    ```  
  
-   B4003 : [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] utilise `netrm:BufferRemaining` pour indiquer combien de nouveaux messages la destination de la messagerie fiable peut mettre en mémoire tampon.  
  
-   B4004 : le [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Service de messagerie fiable limite le nombre de messages transmis lorsque l’application de destination de messagerie fiable ne peut pas recevoir des messages rapidement. La destination de la messagerie fiable met en mémoire tampon les messages et la valeur de l’élément tombe à 0.  
  
-   B4005 : [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] génère des valeurs entières `netrm:BufferRemaining` dans une plage inclusive de 0 à 4096 et lit des valeurs entières dans une plage inclusive de 0 à la valeur `xs:int` 214748364 de `maxInclusive`.  
  
## <a name="message-exchange-patterns"></a>Modèles d'échange de messages  
 Cette section décrit le comportement de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] lorsque la messagerie WS-Reliable est utilisée pour différents modèles d'échange de messages. Pour chaque modèle d'échange de messages, les deux scénarios de déploiements suivants sont considérés :  
  
-   Initiateur non adressable : l'initiateur est derrière un pare-feu ; le répondeur peut remettre des messages à celui-ci uniquement sur les réponses HTTP.  
  
-   Initiateur adressable : l'initiateur et le répondeur peuvent tous les deux recevoir des requêtes HTTP ; en d'autres termes, deux connexions HTTP réciproques peuvent être établies.  
  
### <a name="one-way-non-addressable-initiator"></a>Initiateur unidirectionnel, non adressable  
  
#### <a name="binding"></a>Binding  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] fournit un modèle unidirectionnel d'échange de messages qui utilise une séquence sur un canal HTTP. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] utilise les requêtes HTTP pour transmettre tous les messages du RMS au RMD et la réponse HTTP pour transmettre tous les messages du RMD au RMS.  
  
#### <a name="createsequence-exchange"></a>Échange CreateSequence  
 L'initiateur [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] génère un message `CreateSequence` sans offre. Le répondeur [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] s'assure que `CreateSequence` n'a aucune offre avant de créer une séquence. Le répondeur [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] répond à la demande `CreateSequence` avec un message `CreateSequenceResponse`.  
  
#### <a name="sequenceacknowledgement"></a>SequenceAcknowledgement  
 L'initiateur [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] traite les accusés de réception sur la réponse de tous les messages sauf le message `CreateSequence` et les messages d'erreur. Le répondeur [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] génère toujours un accusé de réception autonome dans la réponse aux messages de séquence et `AckRequested`.  
  
#### <a name="terminatesequence-message"></a>Message TerminateSequence  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] traite `TerminateSequence` comme une opération unidirectionnelle, en d'autres termes, la réponse HTTP a un corps vide et le code d'état HTTP 202.  
  
### <a name="one-way-addressable-initiator"></a>Initiateur unidirectionnel, adressable  
  
#### <a name="binding"></a>Binding  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] fournit un modèle unidirectionnel d'échange de messages qui utilise une séquences sur un canal HTTP entrant et un canal sortant. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] utilise les requêtes HTTP pour transmettre les messages. Toutes les réponses HTTP ont un corps vide et le code d'état HTTP 202.  
  
#### <a name="createsequence-exchange"></a>Échange CreateSequence  
 L'initiateur [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] génère un message `CreateSequence` sans offre. Le répondeur [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] s'assure que `CreateSequence` n'a aucune offre avant de créer une séquence. Le répondeur [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] transmet le message `CreateSequenceResponse` sur une requête HTTP adressée avec la référence de point de terminaison `ReplyTo`.  
  
### <a name="duplex-addressable-initiator"></a>Initiateur duplex, adressable  
  
#### <a name="binding"></a>Binding  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] fournit un modèle d'échange de messages asynchrone complet, bidirectionnel qui utilise deux séquences sur un canal HTTP entrant et sortant. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] utilise les requêtes HTTP pour transmettre les messages. Toutes les réponses HTTP ont un corps vide et le code d'état HTTP 202.  
  
#### <a name="createsequence-exchange"></a>Échange CreateSequence  
 L'initiateur [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] génère un message `CreateSequence` avec une offre. Le répondeur [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] s'assure que `CreateSequence` a une offre avant de créer une séquence. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] envoie `CreateSequenceResponse` sur la requête HTTP adressée à une référence de point de terminaison `CreateSequence` de `ReplyTo`.  
  
#### <a name="sequence-lifetime"></a>Durée de vie de séquence  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] traite les deux séquences comme une session duplex complète.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] s'attend à ce que le point de terminaison distant trouve une erreur dans les deux séquences pour générer une erreur qui fait échouer une séquence. À la lecture d'une erreur qui fait échouer une séquence, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] fait échouer les deux séquences.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] peut fermer sa séquence sortante et continuer à traiter des messages sur sa séquence entrante. Inversement, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] peut traiter la fermeture de la séquence entrante et continuer à envoyer des messages sur sa séquence sortante.  
  
### <a name="request-reply-non-addressable-initiator"></a>Initiateur demande-réponse, non adressable  
  
#### <a name="binding"></a>Binding  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] fournit un modèle unidirectionnel d'échange de messages et de réponse-demande qui utilise deux séquences sur un canal HTTP. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] utilise les requêtes HTTP pour transmettre les messages de la séquence de demande et utilise les réponses HTTP pour transmettre les messages de la séquence de réponse.  
  
#### <a name="createsequence-exchange"></a>Échange CreateSequence  
 L'initiateur [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] génère un message `CreateSequence` avec une offre. Le répondeur [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] s'assure que `CreateSequence` a une offre avant de créer une séquence. Le répondeur [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] répond à la demande `CreateSequence` avec un message `CreateSequenceResponse`.  
  
#### <a name="one-way-message"></a>Message unidirectionnel  
 Pour compléter le protocole d'échange de messages unidirectionnel, l'initiateur [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] transmet un message de séquence de demande sur la requête HTTP et reçoit un message `SequenceAcknowledgement` autonome sur la réponse HTTP. `SequenceAcknowledgement` doit accepter le message transmis.  
  
 Le répondeur [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] peut répondre à la demande avec un accusé de réception, une erreur ou une réponse avec un corps vide et le code d'état HTTP 202.  
  
#### <a name="two-way-messages"></a>Messages bidirectionnels  
 Pour compléter un protocole d'échange de messages bidirectionnel, l'initiateur [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] transmet un message de séquence de demande sur la requête HTTP et reçoit un message de séquence de réponse sur la réponse HTTP. La réponse doit contenir un `SequenceAcknowledgement` qui accuse réception du message de séquence de demande transmis.  
  
 Le répondeur [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] peut répondre à la demande avec une réponse d'application, une erreur ou une réponse avec un corps vide et le code d'état HTTP 202.  
  
 En raison de la présence de messages unidirectionnels et du délai d'attente des réponses d'application, le numéro de séquence du message de séquence de demande et le numéro de séquence du message de réponse n'ont aucune corrélation.  
  
#### <a name="retrying-replies"></a>Nouvelles tentatives de réponses  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] repose sur la corrélation demande-réponse HTTP pour la corrélation de protocole d'échange de messages bidirectionnel. Pour cette raison, l'initiateur [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] n'arrête pas les tentatives pour un message de séquence de demande lorsqu'il y a un accusé de réception pour celui-ci mais arrête les tentatives lorsque la réponse HTTP contient un accusé de réception, un message utilisateur ou une erreur. Le répondeur [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] refait des tentatives de réponse sur le tronçon HTTP de la requête à laquelle la réponse est corrélée.  
  
#### <a name="lastmessage-exchange"></a>Échange LastMessage  
 L'initiateur [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] génère un dernier message vide sur le tronçon de la requête HTTP. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] requiert une réponse, mais ignore le message de réponse réel. Le répondeur [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] répond au dernier message vide de la séquence de demande avec le dernier message vide de la séquence de réponse.  
  
 Si le répondeur [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] reçoit un dernier message dans lequel l'URI action n'est pas http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]il répond avec un dernier message. Dans le cas d'un protocole d'échange de messages bidirectionnel, le dernier message contient le message d'application ; dans le cas d'un protocole d'échange de messages unidirectionnel, le dernier message est vide.  
  
 Le répondeur [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ne requiert pas d'accusé de réception pour le dernier message vide de la séquence de réponse.  
  
#### <a name="terminatesequence-exchange"></a>Échange TerminateSequence  
 Lorsque toutes les demandes ont reçu une réponse valide, l'initiateur [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] génère et transmet le message de séquence de demande `TerminateSequence` sur le tronçon de requête HTTP. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] requiert une réponse, mais ignore le message de réponse réel. Le répondeur [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] répond au message `TerminateSequence` de la séquence de demande avec le message `TerminateSequence` de la séquence de réponse.  
  
 Dans une séquence d'arrêt normale, les deux messages `TerminateSequence` incluent un `SequenceAcknowledgement` complet.  
  
### <a name="requestreply-addressable-initiator"></a>Initiateur demande/réponse, adressable  
  
#### <a name="binding"></a>Binding  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] fournit un modèle d'échange de messages de réponse-demande qui utilise deux séquences sur un canal HTTP entrant et un canal sortant. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] utilise les requêtes HTTP pour transmettre les messages. Toutes les réponses HTTP ont un corps vide et le code d'état HTTP 202.  
  
#### <a name="createsequence-exchange"></a>Échange CreateSequence  
 L'initiateur [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] génère un message `CreateSequence` avec une offre. Le répondeur [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] s'assure que `CreateSequence` a une offre avant de créer une séquence. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] envoie `CreateSequenceResponse` sur la requête HTTP adressée à une référence de point de terminaison `CreateSequence` de `ReplyTo`.  
  
#### <a name="requestreply-correlation"></a>Corrélation demande/réponse  
 L'initiateur [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] s'assure que tous les messages de demande d'application portent un `MessageId` et une référence de point de terminaison `ReplyTo`. L'initiateur [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applique la référence de point de terminaison `CreateSequence` du message `ReplyTo` sur chaque message de demande d'application. Le répondeur [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] requiert que les messages de requête entrants portent un `MessageId` et une référence de point de terminaison `ReplyTo`. Le répondeur [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] s'assure que l'URI de la référence de point de terminaison de `CreateSequence` et de tous les messages de demande d'application est identique.
