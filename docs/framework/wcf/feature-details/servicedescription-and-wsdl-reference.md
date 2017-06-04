---
title: "R&#233;f&#233;rence pour ServiceDescription et WSDL | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: eedc025d-abd9-46b1-bf3b-61d2d5c95fd6
caps.latest.revision: 15
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 15
---
# R&#233;f&#233;rence pour ServiceDescription et WSDL
Cette rubrique décrit comment [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] mappe des documents WSDL \(Web Services Description Language\) à des instances <xref:System.ServiceModel.Description.ServiceDescription> et depuis ces instances.  
  
## Comment ServiceDescription mappe à WSDL 1.1  
 Vous pouvez utiliser [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] pour exporter des documents WSDL à partir d'une instance <xref:System.ServiceModel.Description.ServiceDescription> pour votre service.  Des documents WSDL sont automatiquement générés pour votre service lorsque vous publiez des points de terminaison de métadonnées.  
  
 Vous pouvez également importer des instances <xref:System.ServiceModel.Description.ServiceEndpoint>, des instances <xref:System.ServiceModel.Description.ContractDescription> et des instances <xref:System.ServiceModel.Channels.Binding> à partir de documents WSDL en utilisant le type `WsdlImporter`.  
  
 Les documents WSDL, exportés par [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], importent toute définition de schéma XML utilisée à partir de documents de schéma XML externes.  Un document de schéma XML distinct est exporté pour chaque espace de noms cible utilisé par les types de données dans le service.  De même, un document WSDL distinct est exporté pour chaque espace de noms cible utilisé par les contrats de service.  
  
### ServiceDescription  
 Une instance <xref:System.ServiceModel.Description.ServiceDescription> correspond à un élément `wsdl:service`.  Une instance <xref:System.ServiceModel.Description.ServiceDescription> contient une collection d'instances <xref:System.ServiceModel.Description.ServiceEndpoint> qui correspondent chacune à des éléments `wsdl:port` individuels.  
  
|Propriétés|Mappage WSDL|  
|----------------|------------------|  
|`Name`|Valeur `wsdl:service`\/@name du service.|  
|`Namespace`|TargetNamespace de la définition `wsdl:service` du service.|  
|`Endpoints`|Définitions `wsdl:port` du service.|  
  
### ServiceEndpoint  
 Une instance <xref:System.ServiceModel.Description.ServiceEndpoint> correspond à un élément `wsdl:port`.  Une instance <xref:System.ServiceModel.Description.ServiceEndpoint> contient une adresse, une liaison et un contrat.  
  
 Les comportements de point de terminaison qui implémentent l'interface <xref:System.ServiceModel.Description.IWsdlExportExtension> peuvent modifier l'élément `wsdl:port` du point de terminaison auquel ils sont attachés.  
  
|Propriétés|Mappage WSDL|  
|----------------|------------------|  
|`Name`|Valeur `wsdl:port`\/@name du point de terminaison et valeur `wsdl:binding`\/@name de la liaison de point de terminaison.|  
|`Address`|Adresse de la définition `wsdl:port` du point de terminaison.<br /><br /> Le transport du point de terminaison détermine le format de l'adresse.  Par exemple, pour les transports pris en charge par [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], il peut s'agir d'une adresse SOAP ou d'une référence à un point de terminaison.|  
|`Binding`|Définition `wsdl:binding` du point de terminaison.<br /><br /> À la différence des définitions `wsdl:binding`, les liaisons dans [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ne sont pas liées à un contrat quel qu'il soit.|  
|`Contract`|Définition `wsdl:portType` du point de terminaison.|  
|`Behaviors`|Les comportements de point de terminaison qui implémentent l'interface <xref:System.ServiceModel.Description.IWsdlExportExtension> peuvent modifier l'élément `wsdl:port` du point de terminaison.|  
  
### Liaisons  
 L'instance de liaison d'une instance `ServiceEndpoint` correspond à une définition `wsdl:binding`.  Contrairement aux définitions `wsdl:binding`, qui doivent être associées à une définition `wsdl:portType` spécifique, les liaisons [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sont indépendantes de tout contrat.  
  
 Une liaison est composée d'une collection d'éléments de liaison.  Chaque élément décrit un aspect de la façon dont le point de terminaison communique avec les clients.  En outre, une liaison a un <xref:System.ServiceModel.Channels.MessageVersion> qui indique le <xref:System.ServiceModel.EnvelopeVersion> et le <xref:System.ServiceModel.Channels.AddressingVersion> du point de terminaison.  
  
|Propriétés|Mappage WSDL|  
|----------------|------------------|  
|`Name`|Utilisé dans le nom par défaut d'un point de terminaison, qui est le nom de liaison auquel est ajouté le nom du contrat séparé par un trait de soulignement.|  
|`Namespace`|`targetNamespace` de la définition `wsdl:binding`.<br /><br /> Lors de l'importation, si une stratégie est jointe au port WSDL, l'espace de noms de liaison importé correspond à l'`targetNamespace` de la définition `wsdl:port`.|  
|`BindingElementCollection`, telle que retournée par la méthode `CreateBindingElements`\(\)|Différentes extensions propres au domaine de la définition `wsdl:binding`, généralement des assertions de stratégie.|  
|`MessageVersion`|`EnvelopeVersion` et `AddressingVersion` du point de terminaison.<br /><br /> Lorsque `MessageVersion.None` est spécifié, la liaison WSDL ne contient pas de liaison SOAP et le port WSDL n'a pas de contenu WS\-Addressing.  Ce paramètre est généralement utilisé pour les points de terminaison POX \(Plain Old XML\).|  
  
#### BindingElement  
 Les éléments de liaison d'un point de terminaison de liaison correspondent à différentes extensions WSDL dans la définition `wsdl:binding`, comme des assertions de stratégie.  
  
 Le <xref:System.ServiceModel.Channels.TransportBindingElement> de la liaison détermine l'URI \(Uniform Resource Identifier\) de transport d'une liaison SOAP.  
  
#### AddressingVersion  
 `AddressingVersion` d'une liaison correspond à la version d'adressage utilisée dans la définition `wsd:port`.  [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] prend en charge les adresses SOAP 1.1 et SOAP 1.2, de même que les références de point de terminaison WS\-Addressing 08\/2004 et WS\-Addressing 1.0.  
  
#### EnvelopeVersion  
 `EnvelopeVersion` d'une liaison correspond à la version de SOAP utilisée dans la définition `wsdl:binding`.  [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] prend en charge les liaisons SOAP 1.1 et SOAP 1.2.  
  
### Contrats  
 L'instance <xref:System.ServiceModel.Description.ContractDescription> d'une instance `ServiceEndpoint` correspond à un `wsdl:portType`.  Une instance `ContractDescription` décrit toutes les opérations d'un contrat donné.  
  
|Propriétés|Mappage WSDL|  
|----------------|------------------|  
|`Name`|Valeur `wsdl:portType`\/@name du contrat.|  
|`Namespace`|TargetNamespace de la définition `wsdl:portType`.|  
|`SessionMode`|Valeur `wsdl:portType`\/@msc:usingSession du contrat.  Cet attribut est une extension [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] pour WSDL 1.1.|  
|`Operations`|Définitions `wsdl:operation` du contrat.|  
  
### Opérations  
 Une instance <xref:System.ServiceModel.Description.OperationDescription> correspond à un `wsdl:portType`\/`wsdl:operation`.  Une `OperationDescription` contient une collection d'instances `MessageDescription` qui décrivent les messages de l'opération.  
  
 Deux comportements d'opération participent largement à la manière dont une `OperationDescription` est mappé à un document WSDL : `DataContractSerializerOperationBehavior` et `XmlSerializerOperationBehavior`.  
  
|Propriétés|Mappage WSDL|  
|----------------|------------------|  
|`Name`|Valeur `wsdl:portType`\/`wsdl:operation`\/@name de l'opération.|  
|`ProtectionLevel`|Assertions de protection dans la stratégie de sécurité jointe aux messages `wsdl:binding/wsdl:operation` de cette opération.|  
|`IsInitiating`|Valeur `wsdl:portType`\/`wsdl:operation`\/@msc:isInitiating de l'opération.  Cet attribut est une extension [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] pour WSDL 1.1.|  
|`IsTerminating`|Valeur `wsdl:portType`\/`wsdl:operation`\/@msc:isTerminating de l'opération.  Cet attribut est une extension [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] pour WSDL 1.1.|  
|`Messages`|Messages `wsdl:portType`\/`wsdl:operation`\/`wsdl:input` et `wsdl:portType`\/`wsdl:operation`\/`wsdl:output` de l'opération.|  
|`Faults`|Définitions `wsdl:portType`\/`wsdl:operation`\/`wsdl:fault` de l'opération.|  
|`Behaviors`|Les comportements `DataContractSerializerOperationBehavior` et `XmlSerializerOperationBehavior` gèrent la liaison d'opération et les messages d'opération.|  
  
#### DataContractSerializerOperationBehavior  
 Le comportement `DataContractSerializerOperationBehavior` d'une opération est une implémentation de l'`IWsdlExportExtension` qui exporte les messages WSDL et la liaison de cette opération.  Les types de schémas XML sont exportés à l'aide de l'`XsdDataContractExporter`.  Le comportement `DataContractSerializerOperationBehavior` détermine également l'utilisation, le style, ainsi que l'exportateur et importateur de schéma à utiliser pour cette opération.  
  
|Propriétés|Mappage WSDL|  
|----------------|------------------|  
|`DataContractFormatAttribute`|La propriété `Style` de cet attribut correspond à la valeur `wsdl:binding`\/`wsdl:operation`\/`soap:operation`\/@style de l'opération.<br /><br /> Le comportement `DataContractSerializerOperationBehavior` prend uniquement en charge l'utilisation littérale des types de schémas dans WSDL.|  
  
#### XmlSerializerOperationBehavior  
 Le comportement `XmlSerializerOperationBehavior` d'une opération est une implémentation de l'`IWsdlExportExtension` qui exporte les messages WSDL et la liaison de cette opération.  Les types de schémas XML sont exportés à l'aide de l'`XmlSchemaExporter`.  Le comportement `XmlSerializerOperationBehavior` détermine également l'utilisation, le style, ainsi que l'exportateur et importateur de schéma à utiliser pour cette opération.  
  
|Propriétés|Mappage WSDL|  
|----------------|------------------|  
|`XmlSerializerFormatAttribute`|La propriété `Style` de cet attribut correspond à la valeur `wsdl:binding`\/`wsdl:operation`\/`soap:operation`\/@style de l'opération.<br /><br /> La propriété `Use` de cet attribut correspond à la valeur `wsdl:binding`\/`wsdl:operation`\/`soap:operation`\/\* \/@use de tous les messages de l'opération.|  
  
### Messages  
 Une instance `MessageDescription` correspond à un `wsdl:message` qui est référencé par un message `wsdl:portType`\/`wsdl:operation`\/`wsdl:input` ou `wsdl:portType`\/ `wsdl:operation`\/`wsdl:output` dans une opération.  Une `MessageDescription` possède un corps et des en\-têtes.  
  
|Propriétés|Mappage WSDL|  
|----------------|------------------|  
|`Action`|Action SOAP ou WS\-Addressing du message.<br /><br /> Notez que les opérations qui utilisent la chaîne d'action "\*" ne sont pas représentées dans WSDL.|  
|`Direction`|`MessageDirection.Input` correspond à `wsdl:input`.<br /><br /> `MessageDirection.Output` correspond à `wsdl:output`.|  
|`ProtectionLevel`|Assertions de protection dans la stratégie de sécurité jointe à la définition `wsdl:message` de ce message.|  
|`Body`|Corps du message.|  
|`Headers`|En\-têtes du message.|  
|`ContractDescription.Name`, `OperationContract.Name`|À l'exportation, utilisé pour dériver la valeur `wsdl:message`\/@name.|  
  
#### Corps du message  
 Une instance `MessageBodyDescription` correspond aux définitions `wsdl:message`\/`wsdl:part` du corps d'un message.  Le corps du message peut être encapsulé ou nu.  
  
|Propriétés|Mappage WSDL|  
|----------------|------------------|  
|`WrapperName`|Si le style n'est pas RPC, le `WrapperName` correspond au nom d'élément référencé par le `wsdl:message`\/`wsdl:part`, avec @name ayant la valeur « paramètres ».|  
|`WrapperNamespace`|Si le style n'est pas RPC, l'`WrapperNamespace` correspond à l'espace de noms d'élément du `wsdl:message`\/`wsdl:part`, avec @name ayant la valeur « paramètres ».|  
|`Parts`|Parties du message pour ce corps du message.|  
|`ReturnValue`|Élément enfant de l'élément wrapper si un élément wrapper existe \(style document encapsulé ou style RPC\), sinon premier `wsdl:message`\/`wsdl:part` dans le message.|  
  
#### Parties du message  
 Une instance `MessagePartDescription` correspond à un `wsdl:message`\/`wsdl:part` et au type de schéma XML ou à l'élément vers lequel la partie du message pointe.  
  
|Propriétés|Mappage WSDL|  
|----------------|------------------|  
|`Name`|Valeur `wsd:message`\/`wsdl:part`\/@name de la partie du message et nom de l'élément vers lequel la partie du message pointe.|  
|`Namespace`|Espace de noms de l'élément vers lequel la partie de message pointe.|  
|`Index`|Index du `wsdl:message`\/`wsdl:part` du message.|  
|`ProtectionLevel`|Assertions de protection dans la stratégie de sécurité jointe à la définition `wsdl:message` de cette partie du message.  La stratégie est paramétrée pour pointer vers la partie spécifique du message.|  
|`MessageType`|Type de schéma XML de l'élément vers lequel la partie du message pointe.|  
  
#### En\-têtes de message  
 Une instance `MessageHeaderDescription` est une partie de message qui correspond également à une liaison `soap:header` de la partie du message.  
  
### Erreurs  
 Une instance `FaultDescription` correspond à une définition `wsdl:portType`\/`wsdl:operation`\/`wsdl:fault` et à sa définition `wsdl:message` associée.  La définition `wsdl:message` est ajoutée au même espace de noms cible que son type de port WSDL associé.  La définition `wsdl:message` possède une seule partie de message nommée « détail » qui pointe vers l'élément du schéma XML qui correspond à la valeur de propriété `DefaultType` de l'instance `FaultDescription`.  
  
|Propriétés|Mappage WSDL|  
|----------------|------------------|  
|`Name`|Valeur `wsdl:portType`\/`wsdl:operation`\/`wsdl:fault`\/@name de l'erreur.|  
|`Namespace`|Espace de noms de l'élément du schéma XML vers lequel la partie « détail » du message d'erreur pointe.|  
|`Action`|Action SOAP ou WS\-Addressing de l'erreur.|  
|`ProtectionLevel`|Assertions de protection dans la stratégie de sécurité jointe à la définition `wsdl:message` de cette erreur.|  
|`DetailType`|Type de schéma XML de l'élément vers lequel la partie « détail » du message pointe.|  
|`Name, ContractDescription.Name, OperationDescription.Name,`|Utilisé pour dériver la valeur `wsdl:message`\/@name du message d'erreur.|  
  
## Voir aussi  
 <xref:System.ServiceModel.Description>