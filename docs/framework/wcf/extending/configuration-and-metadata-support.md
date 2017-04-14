---
title: "Prise en charge de la configuration et des m&#233;tadonn&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 27c240cb-8cab-472c-87f8-c864f4978758
caps.latest.revision: 12
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 12
---
# Prise en charge de la configuration et des m&#233;tadonn&#233;es
Cette rubrique décrit comment activer la prise en charge de la configuration et des métadonnées pour les liaisons et éléments de liaison.  
  
## Vue d'ensemble de la configuration et des métadonnées  
 Cette rubrique présente les tâches suivantes, qui correspondent aux éléments facultatifs 1, 2 et 4 de la liste des tâches [Développement de canaux](../../../../docs/framework/wcf/extending/developing-channels.md).  
  
-   Activation de la prise en charge du fichier de configuration pour un élément de liaison.  
  
-   Activation de la prise en charge du fichier de configuration pour une liaison.  
  
-   Exportation des assertions WSDL et de stratégie pour un élément de liaison.  
  
-   Identification des assertions WSDL et de stratégie afin d'insérer et de configurer votre liaison ou élément de liaison.  
  
 Pour plus d'informations sur la création de liaisons définies par l'utilisateur et d'éléments de liaison, consultez [Création de liaisons définies par l'utilisateur](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md) et [Création d'un élément de liaison](../../../../docs/framework/wcf/extending/creating-a-bindingelement.md), respectivement.  
  
## Ajout de la prise en charge de la configuration  
 Pour activer la prise en charge du fichier de configuration pour un canal, vous devez implémenter deux sections de configuration : <xref:System.ServiceModel.Configuration.BindingElementExtensionElement?displayProperty=fullName> qui active la prise en charge de la configuration pour les éléments de liaison, et <xref:System.ServiceModel.Configuration.StandardBindingElement?displayProperty=fullName> et <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602?displayProperty=fullName> qui activent la prise en charge de la configuration pour les liaisons.  
  
 L'un des moyens les plus faciles d'y parvenir consiste à utiliser l'outil exemple [ConfigurationCodeGenerator](../../../../docs/framework/wcf/samples/configurationcodegenerator.md) pour générer le code de configuration pour vos liaisons et éléments de liaison.  
  
### Extension de BindingElementExtensionElement  
 L'exemple de code suivant est extrait de l'exemple [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md).`UdpTransportElement` est un objet <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> qui expose `UdpTransportBindingElement` au système de configuration.Avec quelques substitutions de base, l'exemple définit le nom de section de configuration, le type de l'élément de liaison et la méthode utilisée pour le créer.Les utilisateurs peuvent ensuite enregistrer la section d'extension dans un fichier de configuration comme suit.  
  
```  
<configuration>  
  <system.serviceModel>  
    <extensions>  
      <bindingElementExtensions>  
      <add name="udpTransport" type="Microsoft.ServiceModel.Samples.UdpTransportElement, UdpTransport />  
      </bindingElementExtensions>  
    </extensions>  
  </system.serviceModel>  
</configuration>  
  
```  
  
 L'extension peut être référencée à partir des liaisons personnalisées pour utiliser UDP comme transport.  
  
```  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <customBinding>  
       <binding configurationName="UdpCustomBinding">  
         <udpTransport/>  
       </binding>  
      </customBinding>  
    </bindings>  
  </system.serviceModel>  
</configuration>  
  
```  
  
### Ajout de la configuration pour une liaison  
 La section `SampleProfileUdpBindingCollectionElement` est un <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602> qui expose `SampleProfileUdpBinding` au système de configuration.Le bloc de l'implémentation est délégué à `SampleProfileUdpBindingConfigurationElement`, qui dérive de <xref:System.ServiceModel.Configuration.StandardBindingElement>.`SampleProfileUdpBindingConfigurationElement` a des propriétés qui correspondent à celles sur `SampleProfileUdpBinding`, et des fonctions pour mapper à partir de la liaison `ConfigurationElement` .Enfin, la méthode `OnApplyConfiguration` est substituée dans `SampleProfileUdpBinding`, tel qu'indiqué dans l'exemple de code suivant.  
  
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
  
 Pour enregistrer ce gestionnaire avec le système de configuration, ajoutez la section suivante au fichier de configuration approprié.  
  
```  
<configuration>  
  <configSections>  
     <sectionGroup name="system.serviceModel">  
         <sectionGroup name="bindings">  
                 <section name="sampleProfileUdpBinding" type="Microsoft.ServiceModel.Samples.SampleProfileUdpBindingCollectionElement, UdpTransport />  
         </sectionGroup>  
     </sectionGroup>  
  </configSections>  
</configuration>  
```  
  
 Il pourra ensuite être référencé à partir de la section de configuration [\<system.serviceModel\>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md).  
  
```  
<configuration>  
  <system.serviceModel>  
    <client>  
      <endpoint configurationName="calculator"  
                address="soap.udp://localhost:8001/"   
                bindingConfiguration="CalculatorServer"  
                binding="sampleProfileUdpBinding"   
                contract= "Microsoft.ServiceModel.Samples.ICalculatorContract">  
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
  
```  
  
## Ajout de la prise en charge des métadonnées pour un élément de liaison  
 Pour intégrer un canal dans le système de métadonnées, il doit à la fois prendre en charge l'importation et l'exportation de stratégie.Cela permet aux outils tels que [Outil Service Model Metadata Tool \(Svcutil.exe\)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) de générer des clients de l'élément de liaison.  
  
### Ajout de la prise en charge WSDL  
 L'élément de liaison de transport d'une liaison est chargé d'exporter et d'importer les informations d'adressage dans les métadonnées.Lors de l'utilisation d'une liaison SOAP, l'élément de liaison de transport doit également exporter un URI de transport correct dans les métadonnées.L'exemple de code suivant est extrait de l'exemple [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md).  
  
#### Exportation WSDL  
 Pour exporter des informations d'adressage, `UdpTransportBindingElement` implémente l'interface <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=fullName>.La méthode <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A?displayProperty=fullName> ajoute les informations d'adressage correctes au port WSDL.  
  
```  
if (context.WsdlPort != null)  
{  
    AddAddressToWsdlPort(context.WsdlPort, context.Endpoint.Address, encodingBindingElement.MessageVersion.Addressing);  
}  
```  
  
 L'implémentation `UdpTransportBindingElement` de la méthode <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A> exporte également un URI de transport lorsque le point de terminaison utilise une liaison SOAP :  
  
```  
WsdlNS.SoapBinding soapBinding = GetSoapBinding(context, exporter);  
if (soapBinding != null)  
{  
    soapBinding.Transport = UdpPolicyStrings.UdpNamespace;  
}  
```  
  
#### Importation WSDL  
 Pour étendre le système d'importation WSDL afin de gérer l'importation des adresses, ajoutez la configuration suivante au fichier de configuration de Svcutil.exe, tel qu'indiqué dans le fichier Svcutil.exe.config :  
  
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
  
 Le type `UdpBindingElementImporter` implémente l'interface <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=fullName>.La méthode `ImportEndpoint` importe l'adresse à partir du port WSDL :  
  
```  
BindingElementCollection bindingElements = context.Endpoint.Binding.CreateBindingElements();  
TransportBindingElement transportBindingElement = bindingElements.Find<TransportBindingElement>();  
if (transportBindingElement is UdpTransportBindingElement)  
{  
    ImportAddress(context);  
}  
```  
  
### Ajout de la prise en charge de la stratégie  
 L'élément de liaison personnalisé peut exporter des assertions de stratégie dans la liaison WSDL d'un point de terminaison de service pour exprimer les fonctionnalités de cet élément de liaison.L'exemple de code suivant est extrait de l'exemple [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md).  
  
#### Exportation de stratégie  
 Le type `UdpTransportBindingElement` implémente ``<xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=fullName> pour ajouter la prise en charge de l'exportation de stratégie.En conséquence, <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=fullName> inclut `UdpTransportBindingElement` dans la génération de stratégie des liaisons qui l'incluent.  
  
 Dans <xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A?displayProperty=fullName>, ajoutez une assertion pour UDP et une autre si le canal est en mode multicast.Cela est dû au fait que le mode multicast affecte la manière dont la pile est construite, et doit donc être coordonné entre les deux côtés.  
  
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
  
 Les éléments de liaison de transport personnalisés étant chargés de gérer l'adressage, l'implémentation <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=fullName> sur `UdpTransportBindingElement` doit également gérer l'exportation des assertions de stratégie WS\-Addressing appropriées pour indiquer la version de WS\-Addressing utilisée.  
  
```  
AddWSAddressingAssertion(context, encodingBindingElement.MessageVersion.Addressing);  
```  
  
#### Importation de stratégie  
 Pour étendre le système d'importation de stratégie, ajoutez la configuration suivante au fichier de configuration de Svcutil.exe, tel qu'indiqué dans le fichier Svcutil.exe.config :  
  
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
  
 Puis, implémentez <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=fullName> à partir de la classe enregistrée \(`UdpBindingElementImporter`\).Dans <xref:System.ServiceModel.Description.IPolicyImportExtension.ImportPolicy%2A?displayProperty=fullName>, examinez les assertions dans l'espace de noms approprié et traitez celles permettant de générer le transport et de vérifier s'il est multicast.En outre, supprimez les assertions gérées par l'importateur de la liste des assertions de liaison.Une fois encore, il existe deux méthodes d'intégration possibles lorsque vous exécutez Svcutil.exe :  
  
1.  Pointez Svcutil.exe sur le fichier de configuration en utilisant \/SvcutilConfig:\<fichier\>.  
  
2.  Ajoutez la section de configuration à Svcutil.exe.config dans le répertoire où se trouve Svcutil.exe.  
  
### Ajout d'un importateur de liaison standard personnalisé  
 Par défaut, Svcutil.exe et le type <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=fullName> reconnaissent et importent les liaisons fournies par le système.Sinon, la liaison est importée en tant qu'instance <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=fullName>.Pour permettre à Svcutil.exe et <xref:System.ServiceModel.Description.WsdlImporter> d'importer `SampleProfileUdpBinding`, `UdpBindingElementImporter` agit également comme un importateur de liaison standard personnalisé.  
  
 Un importateur de liaison standard personnalisé implémente la méthode `ImportEndpoint` sur l'interface <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=fullName> pour examiner l'instance <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=fullName> importée à partir des métadonnées afin de vérifier si elle peut avoir été générée par une liaison standard spécifique.  
  
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