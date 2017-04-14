---
title: "D&#233;marrage rapide de la r&#233;solution des probl&#232;mes WCF | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "WCF [WCF], résolution des problèmes"
  - "Windows Communication Foundation [WCF], résolution des problèmes"
ms.assetid: a9ea7a53-f31a-46eb-806e-898e465a4992
caps.latest.revision: 22
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 22
---
# D&#233;marrage rapide de la r&#233;solution des probl&#232;mes WCF
Cette rubrique décrit quelques problèmes connus rencontrés par les clients lorsqu'ils développement des clients et services WCF. Si le problème que vous rencontrez n'est pas répertorié dans la liste, nous vous recommandons de configurer le traçage de votre service. Vous allez ainsi générer un fichier de suivi que vous pourrez consulter à l'aide de la visionneuse dédiée pour obtenir des informations détaillées sur les exceptions pouvant se produire au sein du service. Pour plus d’informations sur la configuration du traçage, consultez [Configuration du suivi](../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md). Pour plus d’informations sur la visionneuse de fichier de traçage, consultez [Service Trace Viewer Tool \(SvcTraceViewer.exe\)](../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).  
  
1.  [Après l'installation de Windows 7 et IIS, lorsque vous tentez d'accéder à un service WCF, vous obtenez le message d'erreur suivant : Erreur HTTP 404.3 –Introuvable](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#bkmk_0)  
  
     Erreur HTTP 404.3 – Introuvable. Impossible d’afficher la page demandée en raison de la configuration d’extension. Si la page est un script, ajoutez un gestionnaire. Si le fichier doit être téléchargé, ajoutez un mappage MIME. Erreur détaillée InformationModule StaticFileModule.  
  
2.  [Je reçois parfois une MessageSecurityException sur la deuxième demande si mon client est inactif pendant un instant après la première demande. Que se passe\-t\-il ?](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q1)  
  
3.  [Mon service commence à rejeter les nouveaux clients une fois qu'environ 10 clients interagissent avec lui. Que se passe\-t\-il ?](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q2)  
  
4.  [Est\-ce que je peux charger la configuration de mon service autrement qu'à partir du fichier de configuration de l'application WCF ?](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q3)  
  
5.  [Mon service et mon client fonctionnent convenablement, mais je ne parviens pas à les faire fonctionner lorsque le client est sur un autre ordinateur. Que se passe\-t\-il ?](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q4)  
  
6.  [Lorsque je lève une FaultException\<Exception\> où le type est une exception, je reçois toujours un type FaultException général sur le client, et non le type générique. Que se passe\-t\-il ?](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q5)  
  
7.  [Il semble que les opérations monodirectionnelles et demande\-réponse reviennent quasiment à la même vitesse lorsque la réponse ne contient pas de données. Que se passe\-t\-il ?](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q6)  
  
8.  [J'utilise un certificat X.509 avec mon service et j'obtiens une System.Security.Cryptography.CryptographicException. Que se passe\-t\-il ?](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q77)  
  
9. [J'ai remplacé les majuscules du premier paramètre d'une opération par des minuscules ; à présent, mon client lève une exception. Que se passe\-t\-il ?](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q88)  
  
10. [J'utilise l'un de mes outils de suivi et j'obtiens une EndpointNotFoundException. Que se passe\-t\-il ?](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q99)  
  
11. [Lors de l'appel d'une application HTTP Web WCF à partir d'une application SOAP WCF, le service retourne l'erreur suivante : 405 Méthode non autorisée](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BK_MK99)  
  
 [Qu'est-ce que l'adresse de base ? Comment est-elle liée à une adresse de point de terminaison ?](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q10)  
  
<a name="bkmk_0"></a>   
## Après l'installation de Windows 7 et IIS, lorsque vous tentez d'accéder à un service WCF, vous obtenez le message d'erreur suivant : Erreur HTTP 404.3 –Introuvable  
 Voici le message d'erreur complet :  
  
 Erreur HTTP 404.3 – Introuvable. Impossible d'afficher la page demandée en raison de la configuration d'extension. Si la page est un script, ajoutez un gestionnaire. Si le fichier doit être téléchargé, ajoutez un mappage MIME. Erreur détaillée InformationModule StaticFileModule.  
  
 Ce message d'erreur se produit lorsque l'« activation HTTP de Windows Communication Foundation » n'est pas explicitement définie dans le Panneau de configuration. Pour cela, dans le Panneau de configuration, cliquez sur Programmes dans le coin inférieur gauche de la fenêtre. Cliquez sur Activer ou désactiver des fonctionnalités Windows. Développez l'élément Microsoft .NET Framework 3.5.1, puis sélectionnez Activation HTTP de Windows Communication Foundation.  
  
<a name="BKMK_q1"></a>   
## Je reçois parfois une MessageSecurityException sur la deuxième demande si mon client est inactif pendant un instant après la première demande. Que se passe\-t\-il ?  
 La deuxième demande peut échouer pour deux raisons principales : \(1\) la session a expiré ou \(2\) le serveur Web qui héberge le service est recyclé. Dans le premier cas, la session est valide jusqu'à ce que le service expire. Lorsque le service ne reçoit pas de demande du client pendant la période spécifiée dans la liaison du service \(<xref:System.ServiceModel.Channels.Binding.ReceiveTimeout%2A>\), le service met fin à la session de sécurité. Les messages clients suivants engendrent une <xref:System.ServiceModel.Security.MessageSecurityException>. Le client doit de nouveau établir une session sécurisée avec le service pour envoyer de futurs messages ou utiliser un jeton de contexte de sécurité avec état. Les jetons de contexte de sécurité avec état permettent également à une session sécurisée de survivre à un serveur Web en cours de recyclage.[!INCLUDE[crabout](../../../includes/crabout-md.md)] l’utilisation de jetons de contexte de sécurité avec état dans une session sécurisée, consultez [Procédure : créer un jeton de contexte de sécurité pour une session sécurisée](../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md). Vous pouvez également désactiver des sessions sécurisées. Lorsque vous utilisez la liaison [\<wsHttpBinding\>](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), vous pouvez affecter à la propriété `establishSecurityContext` la valeur `false` pour désactiver des sessions sécurisées. Pour désactiver des sessions sécurisées pour d'autres liaisons, vous devez créer une liaison personnalisée. Pour plus d’informations sur la création d’une liaison personnalisée, consultez [Comment : créer une liaison personnalisée à l'aide de SecurityBindingElement](../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md). Avant d'appliquer chacune de ces options, vous devez comprendre les conditions de sécurité de votre application.  
  
<a name="BKMK_q2"></a>   
## Mon service commence à rejeter les nouveaux clients une fois qu'environ 10 clients interagissent avec lui. Que se passe\-t\-il ?  
 Par défaut, les services peuvent avoir uniquement 10 sessions simultanées. Par conséquent, si les liaisons de service utilisent des sessions, le service accepte les nouvelles connexions clientes jusqu'à ce qu'il atteigne ce nombre, après quoi il refuse les nouvelles connexions clientes jusqu'à ce que l'une des sessions en cours se termine. Vous pouvez prendre en charge davantage de clients de plusieurs manières. Si votre service ne requiert pas de sessions, n’utilisez pas de liaison avec session. \([!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Utilisation de sessions](../../../docs/framework/wcf/using-sessions.md).\) Une autre option consiste à augmenter la limite de session en changeant la valeur de la propriété <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentSessions%2A> par le nombre approprié à votre situation.  
  
<a name="BKMK_q3"></a>   
## Est\-ce que je peux charger la configuration de mon service autrement qu'à partir du fichier de configuration de l'application WCF ?  
 Oui. Toutefois vous devez créer une classe <xref:System.ServiceModel.ServiceHost> personnalisée qui remplace la méthode <xref:System.ServiceModel.ServiceHostBase.ApplyConfiguration%2A>. À l'intérieur de cette méthode, vous pouvez appeler la base pour charger la configuration en premier \(si vous souhaitez charger également les informations de configuration standard\), mais vous pouvez également remplacer entièrement le système de chargement de la configuration. Notez que si vous souhaitez charger la configuration à partir d'un fichier de configuration différent du fichier de configuration de l'application, vous devez analyser le fichier de configuration vous\-même et charger la configuration.  
  
 L'exemple de code suivant indique la manière de substituer la méthode <xref:System.ServiceModel.ServiceHostBase.ApplyConfiguration%2A> et de configurer directement un point de terminaison.  
  
```  
public class MyServiceHost : ServiceHost  
{  
  public MyServiceHost(Type serviceType, params Uri[] baseAddresses)    
    : base(serviceType, baseAddresses)  
  { Console.WriteLine("MyServiceHost Constructor"); }  
  
  protected override void ApplyConfiguration()  
  {  
    string straddress = GetAddress();  
    Uri address = new Uri(straddress);  
    Binding binding = GetBinding();  
    base.AddServiceEndpoint(typeof(IData), binding, address);  
  }  
  
  string GetAddress()  
  { return "http://MyMachine:7777/MyEndpointAddress/"; }  
  
  Binding GetBinding()  
  {  
    WSHttpBinding binding = new WSHttpBinding();  
    binding.Security.Mode = SecurityMode.None;  
    return binding;  
  }  
}  
```  
  
<a name="BKMK_q4"></a>   
## Mon service et mon client fonctionnent convenablement, mais je ne parviens pas à les faire fonctionner lorsque le client est sur un autre ordinateur. Que se passe\-t\-il ?  
 En fonction de l'exception, plusieurs problèmes peuvent exister :  
  
-   Vous devrez peut\-être remplacer les adresses de point de terminaison du client par le nom d'hôte, au lieu de « localhost ».  
  
-   Vous devrez peut\-être ouvrir le port vers l'application. Pour plus d’informations, consultez [Instructions sur les pare\-feu](../../../docs/framework/wcf/samples/firewall-instructions.md) dans les exemples du Kit de développement logiciel.  
  
-   Pour d’autres problèmes possibles, consultez la rubrique des exemples [Running the Samples in a Workgroup and Across Machines](http://msdn.microsoft.com/fr-fr/a451a525-e7ce-452d-9da9-620221260113).  
  
-   Si votre client utilise des informations d'identification Windows et que l'exception est une <xref:System.ServiceModel.Security.SecurityNegotiationException>, configurez Kerberos comme suit.  
  
    1.  Ajoutez les informations d'identification à l'élément de point de terminaison dans le fichier App.config du client :  
  
        ```  
        <endpoint   
          address="http://MyServer:8000/MyService/"   
          binding="wsHttpBinding"   
          bindingConfiguration="WSHttpBinding_IServiceExample"   
          contract="IServiceExample"   
          behaviorConfiguration="ClientCredBehavior"   
          name="WSHttpBinding_IServiceExample">  
          <identity>  
            <userPrincipalName value="name@corp.contoso.com"/>  
          </identity>  
        </endpoint>  
        ```  
  
    2.  Exécutez le service auto\-hébergé sous le compte System ou NetworkService. Vous pouvez exécuter cette commande pour créer une fenêtre de commande sous le compte System :  
  
        ```  
        at 12:36  /interactive "cmd.exe"  
        ```  
  
    3.  Hébergez le service sous IIS \(Internet Information Services\) qui, par défaut, utilise le compte du nom de principal du service \(SPN\).  
  
    4.  Enregistrez un nouveau SPN avec le domaine à l'aide de SetSPN. Notez que vous devez être administrateur de domaine pour effectuer cette opération.  
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)] le protocole Kerberos, consultez [Concepts de sécurité utilisés dans WCF](../../../docs/framework/wcf/feature-details/security-concepts-used-in-wcf.md) et :  
  
-   [Débogage d'erreurs d'authentification Windows](../../../docs/framework/wcf/feature-details/debugging-windows-authentication-errors.md)  
  
-   [Inscription de noms de principaux du service Kerberos à l’aide de Http.sys](http://go.microsoft.com/fwlink/?LinkId=86943)  
  
-   [Kerberos Explained \(Présentation de Kerberos\)](http://go.microsoft.com/fwlink/?LinkId=86946)  
  
<a name="BKMK_q5"></a>   
## Lorsque je lève une FaultException\<Exception\> où le type est une exception, je reçois toujours un type FaultException général sur le client, et non le type générique. Que se passe\-t\-il ?  
 Il est fortement recommandé de créer votre propre type de données d'erreur personnalisé et de le déclarer comme le type de détail dans votre contrat d'erreur. La raison est que l'utilisation des types d'exceptions fournis par le système :  
  
-   crée une dépendance des types qui supprime l'une des plus grandes forces des applications orientées service ;  
  
-   ne peut pas dépendre d'exceptions sérialisant de manière standard  \(certaines, comme <xref:System.Security.SecurityException> risquent de pas être du tout sérialisables\) ;  
  
-   expose des informations d'implémentation interne aux clients.[!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Spécification et gestion des erreurs dans les contrats et les services](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).  
  
 Si vous déboguez une application, toutefois, vous pouvez sérialiser des informations sur les exceptions et les renvoyer au client à l'aide de la classe <xref:System.ServiceModel.Description.ServiceDebugBehavior>.  
  
<a name="BKMK_q6"></a>   
## Il semble que les opérations monodirectionnelles et demande\-réponse reviennent quasiment à la même vitesse lorsque la réponse ne contient pas de données. Que se passe\-t\-il ?  
 Spécifier qu'une opération est monodirectionnelle signifie uniquement que le contrat de l'opération accepte un message d'entrée et ne renvoie pas de message de sortie. Dans [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], tous les appels clients sont renvoyés lorsque les données sortantes ont été écrites sur le fil ou qu'une exception est levée. Les opérations monodirectionnelles fonctionnent de la même façon et elles peuvent lever si le service ne peut pas être localisé ou bloquer si le service n'est pas préparé à accepter les données du réseau. En général, dans [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], cela provoque des appels monodirectionnels renvoyés au client plus rapidement qu'une demande\-réponse ; mais toute condition qui ralentit l'envoi des données sortantes sur le réseau ralentit les opérations monodirectionnelles ainsi que les opérations demande\-réponse. Voir [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Services monodirectionnels](../../../docs/framework/wcf/feature-details/one-way-services.md) et [Accès aux services à l'aide d'un client WCF](../../../docs/framework/wcf/feature-details/accessing-services-using-a-client.md).  
  
<a name="BKMK_q77"></a>   
## J'utilise un certificat X.509 avec mon service et j'obtiens une System.Security.Cryptography.CryptographicException. Que se passe\-t\-il ?  
 Cela se produit couramment après avoir modifié le compte d'utilisateur sous lequel le processus de travail IIS s'exécute. Par exemple, dans [!INCLUDE[wxp](../../../includes/wxp-md.md)], si vous modifiez le compte d'utilisateur par défaut sous lequel Aspnet\_wp.exe s'exécute en remplaçant ASPNET par un compte d'utilisateur personnalisé, vous pouvez obtenir cette erreur. Lors de l'utilisation d'une clé privée, le processus qui l'utilise aura besoin des autorisations d'accès au fichier qui stocke cette clé.  
  
 Le cas échéant, vous devez octroyer des privilèges d'accès en lecture au compte du processus pour le fichier contenant la clé privée. Par exemple, si le processus de travail IIS s'exécute sous le compte Jacques, vous devrez octroyer à Jacques un accès en lecture au fichier contenant la clé privée.  
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)] sur la manière d’octroyer au compte d’utilisateur l’accès correct au fichier contenant la clé privée pour un certificat X.509 spécifique, consultez [Comment : rendre des certificats X.509 accessibles à WCF](../../../docs/framework/wcf/feature-details/how-to-make-x-509-certificates-accessible-to-wcf.md).  
  
<a name="BKMK_q88"></a>   
## J'ai remplacé les majuscules du premier paramètre d'une opération par des minuscules ; à présent, mon client lève une exception. Que se passe\-t\-il ?  
 La valeur des noms de paramètre dans la signature de l'opération fait partie du contrat et respecte la casse. Utilisez l'attribut <xref:System.ServiceModel.MessageParameterAttribute?displayProperty=fullName> lorsque vous devez distinguer le nom du paramètre local et les métadonnées qui décrivent l'opération pour les applications clientes.  
  
<a name="BKMK_q99"></a>   
## J'utilise l'un de mes outils de suivi et j'obtiens une EndpointNotFoundException. Que se passe\-t\-il ?  
 Si vous utilisez un outil de suivi qui n'est pas le mécanisme de suivi [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] fourni par le système et que vous recevez une <xref:System.ServiceModel.EndpointNotFoundException> qui indique une incompatibilité du filtre d'adresse, vous devez utiliser la classe <xref:System.ServiceModel.Description.ClientViaBehavior> pour diriger les messages vers l'utilitaire de suivi et faire rediriger ces messages par l'utilitaire vers l'adresse du service. La classe <xref:System.ServiceModel.Description.ClientViaBehavior> altère l'en\-tête d'adressage  `Via`  pour spécifier l'adresse réseau suivante séparément du dernier destinataire, indiqué par l'en\-tête d'adressage `To`. Ce faisant, en revanche, ne modifiez pas l'adresse du point de terminaison, utilisée pour établir la valeur `To`.  
  
 L'exemple de code suivant présente un exemple de fichier de configuration d'un client.  
  
```  
<endpoint   
  address=http://localhost:8000/MyServer/  
  binding="wsHttpBinding"  
  bindingConfiguration="WSHttpBinding_IMyContract"  
  behaviorConfiguration="MyClient"   
  contract="IMyContract"   
  name="WSHttpBinding_IMyContract">  
</endpoint>  
<behaviors>  
  <endpointBehaviors>  
    <behavior name="MyClient">  
      <clientVia viaUri="http://localhost:8001/MyServer/"/>  
    </behavior>  
  </endpointBehaviors>  
</behaviors>  
```  
  
<a name="BKMK_q10"></a>   
## Qu'est\-ce que l'adresse de base ? Comment est\-elle liée à une adresse de point de terminaison ?  
 Une adresse de base est l'adresse racine d'une classe <xref:System.ServiceModel.ServiceHost>. Par défaut, si vous ajoutez une classe <xref:System.ServiceModel.Description.ServiceMetadataBehavior> dans votre configuration de service, tous les points de terminaison WSDL \(Web Services Description Language\) que l'hôte publie sont récupérés à partir de l'adresse de base HTTP, plus toute adresse relative fournie au comportement de métadonnées, plus « ?wsdl ». Si vous connaissez bien [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] et IIS, l'adresse de base équivaut au répertoire virtuel.  
  
## Partage d'un port entre un point de terminaison de service et un point de terminaison mex à l'aide de NetTcpBinding  
 Si vous spécifiez l'adresse de base d'un service en tant que net.tcp:\/\/MyServer:8080\/MyService et ajoutez les points de terminaison suivants :  
  
```xml  
<services>  
      <service name="Microsoft.Samples.NetTcp.CalculatorService">  
        <endpoint address="calcsvc" binding ="netTcpBinding" contract="Microsoft.Samples.NetTcp.ICalculator"/>  
        <endpoint address="mex" binding="mexTcpBinding" contract="IMetadataExchange" />  
      </service>  
    </services>  
  
```  
  
 Et si vous modifiez un des paramètres NetTcpBinding comme illustré dans l'extrait de configuration suivant :  
  
```xml  
<bindings>  
      <netTcpBinding>  
        <binding closeTimeout="00:01:00" openTimeout="00:01:00" receiveTimeout="00:10:00" sendTimeout="00:01:00" transactionFlow="false" transferMode="Buffered" transactionProtocol="OleTransactions" hostNameComparisonMode="StrongWildcard" listenBacklog="10" maxBufferPoolSize="524288" maxBufferSize="65536" maxConnections="11" maxReceivedMessageSize="65536">  
          <readerQuotas maxDepth="32" maxStringContentLength="8192" maxArrayLength="16384" maxBytesPerRead="4096" maxNameTableCharCount="16384"/>  
          <reliableSession ordered="true" inactivityTimeout="00:10:00" enabled="false"/>  
          <security mode="Transport">  
            <transport clientCredentialType="Windows" protectionLevel="EncryptAndSign"/>  
          </security>  
        </binding>  
      </netTcpBinding>  
    </bindings>  
  
```  
  
 Un message d'erreur se présentant comme suit s'affiche : Exception non gérée : System.ServiceModel.AddressAlreadyInUseException : Il existe déjà un écouteur sur le point de terminaison IP 0.0.0.0:9000 Vous pouvez contourner cette erreur en spécifiant une URL complète avec un autre port pour le point de terminaison MEX comme illustré dans l'extrait de configuration suivant :  
  
```  
<services>  
      <service name="Microsoft.Samples.NetTcp.CalculatorService">  
        <endpoint address="calcsvc" binding ="netTcpBinding" contract="Microsoft.Samples.NetTcp.ICalculator"/>  
        <endpoint address="net.tcp://localhost:9001/servicemodelsamples/mex" binding="mexTcpBinding" contract="IMetadataExchange" />  
      </service>  
    </services>  
  
```  
  
<a name="BK_MK99"></a>   
## Lors de l'appel d'une application HTTP Web WCF à partir d'une application SOAP WCF, le service retourne l'erreur suivante : 405 Méthode non autorisée  
 Le fait d'appeler une application HTTP Web WCF \(un service qui utilise <xref:System.ServiceModel.WebHttpBinding> et <xref:System.ServiceModel.Description.WebHttpBehavior>\) à partir d'un service WCF peut générer l'exception suivante : `Exception non gérée : System.ServiceModel.FaultException`1[System.ServiceModel.ExceptionDetail] : Le serveur distant a retourné une réponse inattendue : (405) Méthode non autorisée.` Cette exception se produit parce que WCF remplace le <xref:System.ServiceModel.OperationContext> sortant par le <xref:System.ServiceModel.OperationContext> entrant. Pour résoudre ce problème, créez un <xref:System.ServiceModel.OperationContextScope> dans l'opération de service HTTP Web WCF. Exemple :  
  
```ecmascript  
public string Echo(string input)  
        {  
            using (new OperationContextScope(this.InnerChannel))  
            {  
                return base.Channel.Echo(input);  
            }  
        }  
  
```  
  
## Voir aussi  
 [Débogage d'erreurs d'authentification Windows](../../../docs/framework/wcf/feature-details/debugging-windows-authentication-errors.md)