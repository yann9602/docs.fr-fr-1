---
title: "Transport: UDP | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 738705de-ad3e-40e0-b363-90305bddb140
caps.latest.revision: 48
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 48
---
# Transport: UDP
Cet exemple montre comment implémenter le mode unicast et multicast UDP en tant que transport [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] personnalisé.Il décrit la procédure recommandée pour créer un transport personnalisé dans [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], en utilisant l'infrastructure de canal et les meilleures pratiques [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] suivantes.Les étapes de la création d'un transport personnalisé sont les suivantes :  
  
1.  Déterminez le canal [Modèles d'échange de messages](#MessageExchangePatterns) \(IOutputChannel, IInputChannel, IDuplexChannel, IRequestChannel ou IReplyChannel\) que ChannelFactory et ChannelListener prendront en charge.Déterminez ensuite si vous prendrez en charge les variantes de session de ces interfaces.  
  
2.  Créez une fabrication et un écouteur de canal qui prennent en charge votre modèle d'échange de messages.  
  
3.  Assurez\-vous que les exceptions spécifiques au réseau sont normalisées selon la classe dérivée appropriée de <xref:System.ServiceModel.CommunicationException>.  
  
4.  Ajoutez un élément [\<liaison\>](../../../../docs/framework/misc/binding.md) qui ajoute le transport personnalisé à une pile de canaux.Pour plus d'informations, consultez [Ajout d'un élément de liaison](#AddingABindingElement).  
  
5.  Ajoutez une section d'extension d'élément de liaison afin d'exposer le nouvel élément de liaison au système de configuration.  
  
6.  Ajoutez des extensions de métadonnées pour communiquer des fonctionnalités à d'autres points de terminaison.  
  
7.  Ajoutez une liaison qui préconfigure une pile d'éléments de liaison d'après un profil bien défini.Pour plus d'informations, consultez [Ajout d'une liaison standard](#AddingAStandardBinding).  
  
8.  Ajoutez une section de liaison ainsi qu'un élément de configuration de liaison afin d'exposer la liaison au système de configuration.Pour plus d'informations, consultez [Ajout de la prise en charge de la configuration](#AddingConfigurationSupport).  
  
<a name="MessageExchangePatterns"></a>   
## Modèles d'échange de messages  
 La première étape de l'écriture d'un transport personnalisé consiste à déterminer les MEP \(Message Exchange Pattern, modèle d'échange de messages\) requis pour le transport.Trois MEP sont disponibles :  
  
-   Datagramme \(IInputChannel\/IOutputChannel\)  
  
     Lorsque vous utilisez un MEP datagramme, un client envoie un message en utilisant un échange de type « déclenché et oublié » \(fire and forget\).Un échange de ce type requiert une confirmation hors bande de la réussite de la remise.Le message peut être perdu lors de la transmission et ne jamais atteindre le service.Si l'opération d'envoi s'exécute correctement au niveau du client, cela ne garantit pas que le point de terminaison distant a effectivement reçu le message.Le datagramme est un bloc de construction de messagerie fondamental. Vous pouvez en effet définir vos propres protocoles au\-dessus de ce bloc, notamment des protocoles fiables et sécurisés.Les canaux de datagramme du client implémentent l'interface <xref:System.ServiceModel.Channels.IOutputChannel> et ceux du service implémentent l'interface <xref:System.ServiceModel.Channels.IInputChannel>.  
  
-   Demande\-réponse \(IRequestChannel\/IReplyChannel\)  
  
     Dans ce MEP, un message est envoyé et une réponse est reçue.Ce modèle se compose de paires demande\-réponse.Parmi les exemples d'appels demande\-réponse figurent notamment les appels de procédure distante \(RPC\) et les demandes GET de navigateur.Ce modèle est également connu sous le nom de mode semi\-duplex.Dans ce MEP, les canaux du client implémentent <xref:System.ServiceModel.Channels.IRequestChannel> et ceux du service implémentent <xref:System.ServiceModel.Channels.IReplyChannel>.  
  
-   Duplex \(IDuplexChannel\)  
  
     Le MEP duplex permet à un nombre aléatoire de messages d'être envoyés par un client et d'être reçus dans un ordre indifférencié.Le MEP duplex est similaire à une conversation téléphonique, où chaque mot prononcé correspond à un message.Les deux côtés pouvant envoyer et recevoir des messages dans ce MEP, l'interface implémentée par les canaux du client et du service est <xref:System.ServiceModel.Channels.IDuplexChannel>.  
  
 Chacun de ces MEP peut également prendre en charge des sessions.Les fonctionnalités fournies par un canal de session permettent de corréler tous les messages envoyés et reçus sur un canal.Le modèle demande\-réponse correspond à une session autonome à deux messages, la demande et la réponse étant corrélées.En revanche, le modèle demande\-réponse qui prend en charge les sessions implique que toutes les paires demande\/réponse sur ce canal soient corrélées les unes avec les autres.Six MEP sont donc disponibles au total : datagramme, demande\-réponse, duplex, datagramme avec sessions, demande\-réponse avec sessions et duplex avec sessions.  
  
> [!NOTE]
>  Concernant le transport UDP, le seul MEP pris en charge est datagramme, le protocole UDP étant de part nature un protocole de type « déclenché et oublié ».  
  
### ICommunicationObject et cycle de vie des objets WCF  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] a une machine d'état commune permettant de gérer le cycle de vie des objets tels que <xref:System.ServiceModel.Channels.IChannel>, <xref:System.ServiceModel.Channels.IChannelFactory> et <xref:System.ServiceModel.Channels.IChannelListener> utilisés pour la communication.Ces objets de communication peuvent avoir cinq états différents.Ces états sont représentés par l'énumération <xref:System.ServiceModel.CommunicationState> et sont les suivants :  
  
-   Created : état d'un <xref:System.ServiceModel.ICommunicationObject> lorsqu'il est instancié pour la première fois.Aucune entrée\/sortie \(E\/S\) ne se produit dans cet état.  
  
-   Opening : les objets passent à cet état lorsque <xref:System.ServiceModel.ICommunicationObject.Open%2A> est appelé.À ce stade, les propriétés sont rendues immuables, et les entrées\/sorties peuvent commencer.Cette transition est uniquement valide à partir de l'état Created.  
  
-   Opened : les objets passent à cet état lorsque le processus d'ouverture est terminé.Cette transition est uniquement valide à partir de l'état Opening.À ce stade, l'objet est totalement utilisable pour le transfert.  
  
-   Closing : les objets passent à cet état lorsque <xref:System.ServiceModel.ICommunicationObject.Close%2A> est appelé pour un arrêt approprié.Cette transition est uniquement valide à partir de l'état Opened.  
  
-   Closed : dans cet état, les objets ne sont plus utilisables.En général, la configuration est encore accessible pour l'inspection, mais aucune communication ne peut se produire.Cet état est équivalent à la suppression des objets.  
  
-   Faulted : dans cet état, les objets sont accessibles pour l'inspection, mais e sont plus utilisables.Lorsqu'une erreur non récupérable se produit, l'objet passe à cet état.La seule transition valide à partir de cet état est l'état `Closed`.  
  
 Des événements se déclenchent pour chaque transition d'état.La méthode <xref:System.ServiceModel.ICommunicationObject.Abort%2A> peut être appelée à tout moment et provoquer la transition immédiate de l'objet de son état actuel à l'état Closed.L'appel de <xref:System.ServiceModel.ICommunicationObject.Abort%2A> termine toute tâche inachevée.  
  
<a name="ChannelAndChannelListener"></a>   
## Fabrication et écouteur de canal  
 L'étape suivante de l'écriture d'un transport personnalisé consiste à créer une implémentation de <xref:System.ServiceModel.Channels.IChannelFactory> pour les canaux clients et de <xref:System.ServiceModel.Channels.IChannelListener> pour les canaux de service.La couche de canal utilise un modèle de fabrication pour construire des canaux.[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] fournit des assistants de classe de base pour ce processus.  
  
-   La classe <xref:System.ServiceModel.Channels.CommunicationObject> implémente <xref:System.ServiceModel.ICommunicationObject> et applique la machine d'état précédemment décrite à l'étape 2.  
  
-   La classe ``<xref:System.ServiceModel.Channels.ChannelManagerBase> implémente l'objet <xref:System.ServiceModel.Channels.CommunicationObject> et fournit une classe de base unifiée pour les objets <xref:System.ServiceModel.Channels.ChannelFactoryBase> et <xref:System.ServiceModel.Channels.ChannelListenerBase>.La classe <xref:System.ServiceModel.Channels.ChannelManagerBase> fonctionne avec <xref:System.ServiceModel.Channels.ChannelBase>, qui est une classe de base implémentant <xref:System.ServiceModel.Channels.IChannel>.  
  
-   La classe ``<xref:System.ServiceModel.Channels.ChannelFactoryBase> implémente les objets <xref:System.ServiceModel.Channels.ChannelManagerBase> et<xref:System.ServiceModel.Channels.IChannelFactory>, et consolide les surcharges de `CreateChannel` dans une méthode abstraite `OnCreateChannel`.  
  
-   La classe <xref:System.ServiceModel.Channels.ChannelListenerBase> implémente <xref:System.ServiceModel.Channels.IChannelListener>.Elle se charge de la gestion d'état de base.  
  
 Dans cet exemple, l'implémentation de la fabrication est contenue dans UdpChannelFactory.cs et l'implémentation de l'écouteur est contenue dans UdpChannelListener.cs.Les implémentations <xref:System.ServiceModel.Channels.IChannel> sont contenues dans UdpOutputChannel.cs et UdpInputChannel.cs.  
  
### Fabrication de canal UDP  
 `UdpChannelFactory` dérive de <xref:System.ServiceModel.Channels.ChannelFactoryBase>.L'exemple substitue <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> pour fournir un accès à la version de message de l'encodeur de message.L'exemple substitue également <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> afin de nous permettre de détruire notre instance de <xref:System.ServiceModel.Channels.BufferManager> lors des transitions de la machine d'état.  
  
#### Canal de sortie UDP  
 `UdpOutputChannel` implémente <xref:System.ServiceModel.Channels.IOutputChannel>.Le constructeur valide les arguments et construit un objet <xref:System.Net.EndPoint> de destination reposant sur le <xref:System.ServiceModel.EndpointAddress> qui est passé.  
  
```  
this.socket = new Socket(this.remoteEndPoint.AddressFamily, SocketType.Dgram, ProtocolType.Udp);  
  
```  
  
 Le canal peut être fermé de façon appropriée ou incorrecte.Si le canal est fermé de façon appropriée, le socket est fermé et un appel à la méthode `OnClose` de la classe de base est effectué.Si une exception est levée, l'infrastructure appelle `Abort` pour s'assurer que le canal est nettoyé.  
  
```  
this.socket.Close(0);  
  
```  
  
 Nous implémentons ensuite `Send()` et `BeginSend()`\/`EndSend()`.Deux phases peuvent alors être distinguées.Tout d'abord, la sérialisation du message dans un tableau d'octets.  
  
```  
ArraySegment<byte> messageBuffer = EncodeMessage(message);  
  
```  
  
 Puis, l'envoi des données résultantes sur le câble.  
  
```  
this.socket.SendTo(messageBuffer.Array, messageBuffer.Offset, messageBuffer.Count, SocketFlags.None, this.remoteEndPoint);  
```  
  
### UdpChannelListener  
 L'élément``UdpChannelListener implémenté par l'exemple dérive de la classe <xref:System.ServiceModel.Channels.ChannelListenerBase>.Il utilise un socket UDP unique pour recevoir des datagrammes.La méthode `OnOpen` reçoit des données à l'aide du socket UDP dans une boucle asynchrone.Les données sont ensuite converties en messages à l'aide de l'infrastructure d'encodage de message.  
  
```  
message = MessageEncoderFactory.Encoder.ReadMessage(new ArraySegment<byte>(buffer, 0, count), bufferManager);  
```  
  
 Étant donné que le même canal de datagramme représente des messages qui arrivent de plusieurs sources, `UdpChannelListener` est un écouteur singleton.Il y a, au plus, un objet <xref:System.ServiceModel.Channels.IChannel>``actif associé à cet écouteur à la fois.L'exemple en génère un autre uniquement si un canal retourné par la méthode `AcceptChannel` est supprimé par la suite.Lorsqu'un message est reçu, il est mis en file d'attente dans ce canal singleton.  
  
#### UdpInputChannel  
 La classe `UdpInputChannel` implémente `IInputChannel`.Elle se compose d'une file d'attente de messages entrants remplie par le socket de `UdpChannelListener`.Ces messages sont extraits de la file d'attente par la méthode `IInputChannel.Receive```.  
  
<a name="AddingABindingElement"></a>   
## Ajout d'un élément de liaison  
 Maintenant que les fabrications de canaux sont construites, nous devons les exposer à l'exécution de ServiceModel via une liaison.Une liaison est une collection d'éléments de liaison qui représente la pile de communication associée à une adresse de service.Chaque élément de la pile est représenté par un élément [\<liaison\>](../../../../docs/framework/misc/binding.md).  
  
 Dans notre exemple, l'élément de liaison est `UdpTransportBindingElement`, lequel dérive de <xref:System.ServiceModel.Channels.TransportBindingElement>.Il substitue les méthodes suivantes pour générer les fabrications associées à notre liaison.  
  
```  
public IChannelFactory<TChannel> BuildChannelFactory<TChannel>(BindingContext context)  
{  
            return (IChannelFactory<TChannel>)(object)new UdpChannelFactory(this, context);  
}  
  
public IChannelListener<TChannel> BuildChannelListener<TChannel>(BindingContext context)  
{  
            return (IChannelListener<TChannel>)(object)new UdpChannelListener(this, context);  
}  
```  
  
 Il contient également des membres permettant de cloner `BindingElement` et de retourner notre schéma \(soap.udp\).  
  
## Ajout de la prise en charge des métadonnées pour un élément de liaison de transport  
 Pour intégrer notre transport dans le système de métadonnées, nous devons prendre à la fois en charge l'importation et l'exportation de stratégie.Cela nous permet de générer des clients de notre liaison via [Outil Service Model Metadata Tool \(Svcutil.exe\)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
### Ajout de la prise en charge WSDL  
 L'élément de liaison de transport d'une liaison est chargé d'exporter et d'importer les informations d'adressage dans les métadonnées.Lors de l'utilisation d'une liaison SOAP, l'élément de liaison de transport doit également exporter un URI de transport correct dans les métadonnées.  
  
#### Exportation WSDL  
 Pour exporter des informations d'adressage, `UdpTransportBindingElement` implémente l'interface `IWsdlExportExtension`.La méthode `ExportEndpoint` ajoute les informations d'adressage correctes au port WSDL.  
  
```  
if (context.WsdlPort != null)  
{  
    AddAddressToWsdlPort(context.WsdlPort, context.Endpoint.Address, encodingBindingElement.MessageVersion.Addressing);  
}  
```  
  
 L'implémentation `UdpTransportBindingElement` de la méthode `ExportEndpoint` exporte également un URI de transport lorsque le point de terminaison utilise une liaison SOAP.  
  
```  
WsdlNS.SoapBinding soapBinding = GetSoapBinding(context, exporter);  
if (soapBinding != null)  
{  
    soapBinding.Transport = UdpPolicyStrings.UdpNamespace;  
}  
```  
  
#### Importation WSDL  
 Pour étendre le système d'importation WSDL afin de gérer l'importation des adresses, nous devons ajouter la configuration suivante au fichier de configuration de Svcutil.exe, tel qu'indiqué dans le fichier Svcutil.exe.config.  
  
```  
<configuration>  
  <system.serviceModel>  
    <client>  
      <metadata>  
        <wsdlImporters>  
          <extension type=" Microsoft.ServiceModel.Samples.UdpBindingElementImporter, UdpTransport" />  
        </policyImporters>  
      </metadata>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
 Lorsque vous exécutez Svcutil.exe, deux méthodes permettent de faire en sorte que Svcutil.exe charge les extensions d'importation WSDL :  
  
1.  Pointez Svcutil.exe sur le fichier de configuration en utilisant \/SvcutilConfig:\<fichier\>.  
  
2.  Ajoutez la section de configuration à Svcutil.exe.config dans le répertoire où se trouve Svcutil.exe.  
  
 Le type `UdpBindingElementImporter` implémente l'interface `IWsdlImportExtension`.La méthode `ImportEndpoint` importe l'adresse à partir du port WSDL.  
  
```  
BindingElementCollection bindingElements = context.Endpoint.Binding.CreateBindingElements();  
TransportBindingElement transportBindingElement = bindingElements.Find<TransportBindingElement>();  
if (transportBindingElement is UdpTransportBindingElement)  
{  
    ImportAddress(context);  
}  
```  
  
### Ajout de la prise en charge de la stratégie  
 L'élément de liaison personnalisé peut exporter des assertions de stratégie dans la liaison WSDL d'un point de terminaison de service pour exprimer les fonctionnalités de cet élément de liaison.  
  
#### Exportation de stratégie  
 Le type `UdpTransportBindingElement` implémente```IPolicyExportExtension` pour ajouter la prise en charge de l'exportation de stratégie.En conséquence, `System.ServiceModel.MetadataExporter` inclut `UdpTransportBindingElement` dans la génération de stratégie des liaisons qui l'incluent.  
  
 Dans `IPolicyExportExtension.ExportPolicy`, nous ajoutons une assertion pour UDP et une autre si nous sommes en mode multicast.Cela est dû au fait que le mode multicast affecte la manière dont la pile est construite, et doit donc être coordonné entre les deux côtés.  
  
```  
ICollection<XmlElement> bindingAssertions = context.GetBindingAssertions();  
XmlDocument xmlDocument = new XmlDocument();  
bindingAssertions.Add(xmlDocument.CreateElement(  
UdpPolicyStrings.Prefix, UdpPolicyStrings.TransportAssertion, UdpPolicyStrings.UdpNamespace));  
if (Multicast)  
{  
    bindingAssertions.Add(xmlDocument.CreateElement(  
UdpPolicyStrings.Prefix, UdpPolicyStrings.MulticastAssertion,     UdpPolicyStrings.UdpNamespace));  
}  
```  
  
 Les éléments de liaison de transport personnalisés étant chargés de gérer l'adressage, l'implémentation `IPolicyExportExtension` sur `UdpTransportBindingElement` doit également gérer l'exportation des assertions de stratégie WS\-Addressing appropriées pour indiquer la version de WS\-Addressing utilisée.  
  
```  
AddWSAddressingAssertion(context, encodingBindingElement.MessageVersion.Addressing);  
```  
  
#### Importation de stratégie  
 Pour étendre le système d'importation de stratégie, nous devons ajouter la configuration suivante au fichier de configuration de Svcutil.exe, tel qu'indiqué dans le fichier Svcutil.exe.config.  
  
```  
<configuration>  
  <system.serviceModel>  
    <client>  
      <metadata>  
        <policyImporters>  
          <extension type=" Microsoft.ServiceModel.Samples.UdpBindingElementImporter, UdpTransport" />  
        </policyImporters>  
      </metadata>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
 Puis nous implémentons `IPolicyImporterExtension` à partir de la classe enregistrée \(`UdpBindingElementImporter`\).Dans `ImportPolicy()`, nous examinons les assertions dans notre espace de noms, puis traitons celles permettant de générer le transport et vérifions s'il est multicast.Nous devons également supprimer les assertions que nous gérons de la liste des assertions de liaison.Une fois encore, il existe deux méthodes d'intégration possibles lorsque vous exécutez Svcutil.exe :  
  
1.  Pointez Svcutil.exe sur le fichier de configuration en utilisant \/SvcutilConfig:\<fichier\>.  
  
2.  Ajoutez la section de configuration à Svcutil.exe.config dans le répertoire où se trouve Svcutil.exe.  
  
<a name="AddingAStandardBinding"></a>   
## Ajout d'une liaison standard  
 Notre élément de liaison peut être utilisé des deux façons suivantes :  
  
-   Via une liaison personnalisée : une liaison personnalisée permet à l'utilisateur de créer sa propre la liaison en fonction d'un ensemble arbitraire d'éléments de liaison.  
  
-   En utilisant une liaison fournie par le système qui inclut notre élément de liaison.[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] fournit un certains nombre de ces liaisons définies par le système, telles que `BasicHttpBinding`, `NetTcpBinding` et `WsHttpBinding`.Chacune de ces liaisons est associée à un profil bien défini.  
  
 L'exemple implémente la liaison de profil dans `SampleProfileUdpBinding`, lequel dérive de <xref:System.ServiceModel.Channels.Binding>.`SampleProfileUdpBinding` contient jusqu'à quatre éléments de liaison : `UdpTransportBindingElement`, `TextMessageEncodingBindingElement CompositeDuplexBindingElement` et `ReliableSessionBindingElement`.  
  
```  
public override BindingElementCollection CreateBindingElements()  
{     
    BindingElementCollection bindingElements = new BindingElementCollection();  
    if (ReliableSessionEnabled)  
    {  
        bindingElements.Add(session);  
        bindingElements.Add(compositeDuplex);  
    }  
    bindingElements.Add(encoding);  
    bindingElements.Add(transport);  
    return bindingElements.Clone();  
}  
```  
  
### Ajout d'un importateur de liaison standard personnalisé  
 Par défaut, Svcutil.exe et le type `WsdlImporter` reconnaissent et importent les liaisons définies par le système.Sinon, la liaison est importée en tant qu'instance `CustomBinding`.Pour permettre à Svcutil.exe et `WsdlImporter` d'importer `SampleProfileUdpBinding`, `UdpBindingElementImporter` agit également comme un importateur de liaison standard personnalisé.  
  
 Un importateur de liaison standard personnalisé implémente la méthode `ImportEndpoint` sur l'interface `IWsdlImportExtension` pour examiner l'instance `CustomBinding` importée à partir des métadonnées afin de vérifier si elle peut avoir été générée par une liaison standard spécifique.  
  
```  
if (context.Endpoint.Binding is CustomBinding)  
{  
    Binding binding;  
    if (transportBindingElement is UdpTransportBindingElement)  
    {  
        //if TryCreate is true, the CustomBinding will be replace by a SampleProfileUdpBinding in the  
        //generated config file for better typed generation.  
        if (SampleProfileUdpBinding.TryCreate(bindingElements, out binding))  
        {  
            binding.Name = context.Endpoint.Binding.Name;  
            binding.Namespace = context.Endpoint.Binding.Namespace;  
            context.Endpoint.Binding = binding;  
        }  
    }  
}  
```  
  
 En général, l'implémentation d'un importateur de liaison standard personnalisé implique la vérification des propriétés des éléments de liaison importés afin de s'assurer que seules les propriétés pouvant avoir été définies par la liaison standard ont été modifiées et que toutes les autres ont été définies à leurs valeurs par défaut.L'une des stratégies de base permettant d'implémenter un importateur de liaison standard consiste à créer une instance de la liaison standard, à propager les propriétés des éléments de liaison vers l'instance de liaison standard que la liaison standard prend en charge, et à comparer les éléments de liaison de la liaison standard avec les éléments de liaison importés.  
  
<a name="AddingConfigurationSupport"></a>   
## Ajout de la prise en charge de la configuration  
 Pour exposer notre transport via la configuration, nous devons implémenter deux sections de configuration.La première est `BindingElementExtensionElement` pour `UdpTransportBindingElement`.C'est de cette façon que les implémentations `CustomBinding` référencent notre élément de liaison.La deuxième est `Configuration` pour `SampleProfileUdpBinding`.  
  
### Élément d'extension de l'élément de liaison  
 La section`````UdpTransportElement` est un objet `BindingElementExtensionElement` qui expose `UdpTransportBindingElement` au système de configuration.Avec quelques substitutions de base, nous définissons le nom de notre section de configuration, le type de notre élément de liaison et la méthode utilisée pour le créer.Nous pouvons ensuite enregistrer notre section d'extension dans un fichier de configuration, tel qu'indiqué dans le code suivant.  
  
```  
<configuration>  
  \<system.serviceModel>  
    <extensions>  
      <bindingElementExtensions>  
      \<add name="udpTransport" type="Microsoft.ServiceModel.Samples.UdpTransportElement, UdpTransport />  
      </bindingElementExtensions>  
    </extensions>  
  \</system.serviceModel>  
</configuration>  
  
```  
  
 L'extension peut être référencée à partir des liaisons personnalisées pour utiliser UDP comme transport.  
  
```  
<configuration>  
  \<system.serviceModel>  
    <bindings>  
      <customBinding>  
       <binding configurationName="UdpCustomBinding">  
         <udpTransport/>  
       </binding>  
      </customBinding>  
    </bindings>  
  \</system.serviceModel>  
</configuration>  
  
```  
  
### Section de liaison  
 La section `SampleProfileUdpBindingCollectionElement` est un `StandardBindingCollectionElement` qui expose `SampleProfileUdpBinding` au système de configuration.Le bloc de l'implémentation est délégué à `SampleProfileUdpBindingConfigurationElement`, qui dérive de `StandardBindingElement`.`SampleProfileUdpBindingConfigurationElement` a des propriétés qui correspondent à celles sur `SampleProfileUdpBinding`, et des fonctions pour mapper à partir de la liaison `ConfigurationElement` .Enfin, nous substituons `OnApplyConfiguration` dans notre `SampleProfileUdpBinding`, tel qu'indiqué dans l'exemple de code suivant.  
  
```  
protected override void OnApplyConfiguration(string configurationName)  
{  
            if (binding == null)  
                throw new ArgumentNullException("binding");  
  
            if (binding.GetType() != typeof(SampleProfileUdpBinding))  
            {  
                throw new ArgumentException(string.Format(CultureInfo.CurrentCulture,  
                    "Invalid type for binding. Expected type: {0}. Type passed in: {1}.",  
                    typeof(SampleProfileUdpBinding).AssemblyQualifiedName,  
                    binding.GetType().AssemblyQualifiedName));  
            }  
            SampleProfileUdpBinding udpBinding = (SampleProfileUdpBinding)binding;  
  
            udpBinding.OrderedSession = this.OrderedSession;  
            udpBinding.ReliableSessionEnabled = this.ReliableSessionEnabled;  
            udpBinding.SessionInactivityTimeout = this.SessionInactivityTimeout;  
            if (this.ClientBaseAddress != null)  
                   udpBinding.ClientBaseAddress = ClientBaseAddress;  
}  
  
```  
  
 Pour enregistrer ce gestionnaire avec le système de configuration, nous ajoutons la section suivante au fichier de configuration approprié.  
  
```  
<configuration>  
  <configSections>  
     <sectionGroup name="system.serviceModel">  
         <sectionGroup name="bindings">  
                 \<section name="sampleProfileUdpBinding" type="Microsoft.ServiceModel.Samples.SampleProfileUdpBindingCollectionElement, UdpTransport />  
         </sectionGroup>  
     </sectionGroup>  
  </configSections>  
</configuration>  
```  
  
 Il pourra ensuite être référencé à partir de la section de configuration serviceModel.  
  
```  
<configuration>  
  \<system.serviceModel>  
    <client>  
      <endpoint configurationName="calculator"  
                address="soap.udp://localhost:8001/"   
                bindingConfiguration="CalculatorServer"  
                binding="sampleProfileUdpBinding"   
                contract= "Microsoft.ServiceModel.Samples.ICalculatorContract">  
      </endpoint>  
    </client>  
  \</system.serviceModel>  
</configuration>  
```  
  
## Client et service de test UDP  
 Le code de test permettant d'utiliser cet exemple de transport est disponible dans les répertoires UdpTestService et UdpTestClient.Le code de service se compose de deux tests : le premier définit les liaisons et les points de terminaison à partir du code, et le deuxième le fait via la configuration.Ces deux tests utilisent deux points de terminaison.Un point de terminaison utilise `SampleUdpProfileBinding` avec [\<reliableSession\>](http://msdn.microsoft.com/fr-fr/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b) à la valeur `true`.L'autre utilise une liaison personnalisée avec `UdpTransportBindingElement`.Cela revient à utiliser `SampleUdpProfileBinding` avec [\<reliableSession\>](http://msdn.microsoft.com/fr-fr/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b) à la valeur `false`.Ces deux tests créent un service, ajoutent  un point de terminaison pour chaque liaison, ouvrent le service, puis attendent que l'utilisateur tape ENTER avant de fermer le service.  
  
 Lorsque vous démarrez l'application de test de service, la sortie suivante doit s'afficher.  
  
```  
Testing Udp From Code.  
Service is started from code...  
Press <ENTER> to terminate the service and start service from config...  
```  
  
 Vous pouvez ensuite exécuter l'application de test cliente sur les points de terminaison publiés.L'application de test cliente crée un client pour chaque point de terminaison et envoie cinq messages à chacun.Sortie sur le client :  
  
```  
Testing Udp From Imported Files Generated By SvcUtil.  
0  
3  
6  
9  
12  
Press <ENTER> to complete test.  
```  
  
 Sortie complète sur le service :  
  
```  
Service is started from code...  
Press <ENTER> to terminate the service and start service from config...  
Hello, world!  
Hello, world!  
Hello, world!  
Hello, world!  
Hello, world!  
   adding 0 + 0  
   adding 1 + 2  
   adding 2 + 4  
   adding 3 + 6  
   adding 4 + 8  
```  
  
 Pour exécuter l'application cliente sur des points de terminaison publiés à l'aide de la configuration, tapez ENTER sur le service, puis exécutez de nouveau le client test.La sortie suivante doit s'afficher sur le service.  
  
```  
Testing Udp From Config.  
Service is started from config...  
Press <ENTER> to terminate the service and exit...  
```  
  
 La réexécution du client génère les mêmes résultats que ceux obtenus précédemment.  
  
 Pour régénérer le code client et la configuration à l'aide de Svcutil.exe, démarrez l'application de service, puis exécutez le fichier Svcutil.exe suivant à partir du répertoire racine de l'exemple.  
  
```  
svcutil http://localhost:8000/udpsample/ /reference:UdpTranport\bin\UdpTransport.dll /svcutilConfig:svcutil.exe.config  
```  
  
 Svcutil.exe ne générant pas de configuration d'extension de liaison pour `SampleProfileUdpBinding`, vous devez donc l'ajouter manuellement.  
  
```  
<configuration>  
    \<system.serviceModel>      
        …  
        <extensions>  
            \<!-- This was added manually because svcutil.exe does not add this extension to the file -->  
            <bindingExtensions>  
                <add name="sampleProfileUdpBinding" type="Microsoft.ServiceModel.Samples.SampleProfileUdpBindingCollectionElement, UdpTransport" />  
            </bindingExtensions>  
        </extensions>  
    \</system.serviceModel>  
</configuration>  
```  
  
#### Pour configurer, générer et exécuter l'exemple  
  
1.  Pour générer la solution, suivez les instructions indiquées dans [Génération des exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2.  Pour exécuter l'exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions indiquées dans [Exécution des exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
3.  Référez\-vous à la section « Client et service de test UDP » développée précédemment.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur.Recherchez le répertoire \(par défaut\) suivant avant de continuer.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, rendez\-vous sur la page \(éventuellement en anglais\) des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WCF\Extensibility\Transport\Udp`  
  
## Voir aussi