---
title: "Attributs ServiceModel et référence ServiceDescription"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4ab86b17-eab9-4846-a881-0099f9a7cc64
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 61a0811176a5db17e040073d031fa50865a09857
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="servicemodel-attributes-and-servicedescription-reference"></a>Attributs ServiceModel et référence ServiceDescription
Le *arborescence de description* correspond à la hiérarchie de types (commençant par la <xref:System.ServiceModel.Description.ServiceDescription?displayProperty=nameWithType> classe) qui décrivent ensemble chaque aspect d’un service. [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] utilise une arborescence de description pour générer une exécution du service valide, pour publier le langage WSDL (Web Services Description Language), le langage XSD (XML Schema Definition Language) et les assertions de stratégie (métadonnées) concernant le service qui permettent aux clients de s'y connecter et de l'utiliser, et pour générer diverses représentations de code et de fichier de configuration des valeurs de l'arborescence de description.  
  
 Cette rubrique décrit comment obtenir les propriétés relatives au contrat à partir du contrat de service, et la manière dont elles sont implémentées et ajoutées à l'arborescence de description. Dans certains cas, les valeurs d’attribut sont converties en propriétés de comportement et le comportement est ensuite inséré dans l’arborescence de description. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]manière dont les valeurs d’arborescence de description sont converties dans les métadonnées, consultez [ServiceDescription et WSDL référence](../../../../docs/framework/wcf/feature-details/servicedescription-and-wsdl-reference.md).  
  
## <a name="mapping-operations-to-the-description-tree"></a>Mappage des opérations à l’arborescence de description  
 Dans les applications [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], les contrats de service sont modélisés par les interfaces (ou classes) qui utilisent des attributs pour marquer l'interface ou la classe et ses méthodes sous forme d'un regroupement d'opérations. Lorsqu'une classe <xref:System.ServiceModel.ServiceHost> est ouverte, les implémentations et les contrats de service sont pris en compte dans, et fusionnées avec, les informations de configuration dans une arborescence de description.  
  
 Il existe deux types de modèles d’opération : le *paramètre* modèle et le *contrat de message* modèle. Le modèle de paramètre utilise des méthodes managées qui n'ont pas de type de paramètre ou de valeur de retour marqué par la classe <xref:System.ServiceModel.MessageContractAttribute?displayProperty=nameWithType>. Dans ce modèle, les développeurs contrôlent la sérialisation des paramètres et des valeurs de retour, mais [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] génère les valeurs utilisées pour remplir l'arborescence de description du service et de son contrat.  
  
 Les liaisons spécifiées dans les fichiers de configuration sont directement chargées dans la propriété <xref:System.ServiceModel.Description.ServiceEndpoint.Binding%2A?displayProperty=nameWithType>.  
  
|Propriété ServiceBehaviorAttribute|Valeur de l’arborescence de description affectée|  
|---------------------------------------|-------------------------------------|  
|Name|<xref:System.ServiceModel.Description.ServiceDescription.Name%2A>|  
|Espace de noms|<xref:System.ServiceModel.Description.ServiceDescription.Namespace%2A>|  
|ConfigurationName|<xref:System.ServiceModel.Description.ServiceDescription.ConfigurationName%2A>|  
|IgnoreExtensionDataObject|Définit la propriété <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior.IgnoreExtensionDataObject%2A> de toutes les opérations.|  
|MaxItemsInObjectGraph|Définit la propriété <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior.MaxItemsInObjectGraph%2A> de toutes les opérations.|  
  
|Propriété ServiceContractAttribute|Valeur de l’arborescence de description affectée|  
|---------------------------------------|-------------------------------------|  
|CallbackContract|<xref:System.ServiceModel.Description.ContractDescription.CallbackContractType%2A>, <xref:System.ServiceModel.Description.MessageDescription> ajoutés à toutes les opérations <xref:System.ServiceModel.Description.OperationDescription.Messages%2A>.|  
|ConfigurationName|<xref:System.ServiceModel.Description.ContractDescription.ConfigurationName%2A>|  
|ProtectionLevel|<xref:System.ServiceModel.Description.ContractDescription.ProtectionLevel%2A> et éventuellement des niveaux de protection enfants. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]la hiérarchie du niveau de protection, consultez [au niveau de Protection de présentation](../../../../docs/framework/wcf/understanding-protection-level.md).|  
|SessionMode|<xref:System.ServiceModel.Description.ContractDescription.SessionMode%2A>|  
  
|Valeur ServiceKnownTypesAttribute|Valeur de l'arborescence de description affectée|  
|--------------------------------------|-------------------------------------|  
|MethodName|<xref:System.ServiceModel.Description.OperationDescription.KnownTypes%2A>|  
  
|Valeur OperationContractAttribute|Valeur de l’arborescence de description affectée|  
|--------------------------------------|-------------------------------------|  
|Action|<xref:System.ServiceModel.Description.MessageDescription.Action%2A> pour le message de sortie ou d'entrée, selon le contrat/contrat de rappel.|  
|AsyncPattern|Si la valeur est true, <xref:System.ServiceModel.Description.OperationDescription.BeginMethod%2A> et <xref:System.ServiceModel.Description.OperationDescription.EndMethod%2A>|  
|IsOneWay|Mappe à un <xref:System.ServiceModel.Description.MessageDescription> unique dans <xref:System.ServiceModel.Description.OperationDescription.Messages%2A>|  
|IsInitiating|<xref:System.ServiceModel.Description.OperationDescription.IsInitiating%2A>|  
|IsTerminating|<xref:System.ServiceModel.Description.OperationDescription.IsTerminating%2A>|  
|Name|<xref:System.ServiceModel.Description.OperationDescription.Name%2A>|  
|ProtectionLevel|<xref:System.ServiceModel.Description.OperationDescription.ProtectionLevel%2A> et éventuellement des niveaux de protection enfants. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]la hiérarchie du niveau de protection, consultez [au niveau de Protection de présentation](../../../../docs/framework/wcf/understanding-protection-level.md).|  
|ReplyAction|<xref:System.ServiceModel.Description.MessageDescription.Action%2A> pour le message de sortie ou d'entrée, selon le contrat/contrat de rappel.|  
  
|Valeur FaultContractAttribute|Valeur de l’arborescence de description affectée|  
|----------------------------------|-------------------------------------|  
|Action|<xref:System.ServiceModel.Description.FaultDescription.Action%2A> selon le contrat/contrat de rappel.|  
|DetailType|<xref:System.ServiceModel.Description.FaultDescription.DetailType%2A>|  
|Name|<xref:System.ServiceModel.Description.FaultDescription.Name%2A>|  
|Espace de noms|<xref:System.ServiceModel.Description.FaultDescription.Namespace%2A>|  
|ProtectionLevel|<xref:System.ServiceModel.Description.FaultDescription.ProtectionLevel%2A>|  
  
|Valeur DataContractFormatAttribute|Valeur de l’arborescence de description affectée|  
|---------------------------------------|-------------------------------------|  
|Utilisez|La valeur <xref:System.ServiceModel.DataContractFormatAttribute.Style%2A> est définie sur le <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> de l'opération.|  
  
|Valeur XmlSerializerFormatAttribute|Valeur de l’arborescence de description affectée|  
|----------------------------------------|-------------------------------------|  
|Style|Cette propriété <xref:System.ServiceModel.XmlSerializerFormatAttribute> est définie sur le <xref:System.ServiceModel.Description.XmlSerializerOperationBehavior> de l'opération.|  
|Utilisez|<xref:System.ServiceModel.XmlSerializerFormatAttribute> est définie sur le <xref:System.ServiceModel.Description.XmlSerializerOperationBehavior> de l'opération.|  
  
|Valeur TransactionFlowAttribute|Valeur de l’arborescence de description affectée|  
|------------------------------------|-------------------------------------|  
|TransactionFlowOption|<xref:System.ServiceModel.TransactionFlowAttribute> est ajouté comme comportement d'opération à la propriété <xref:System.ServiceModel.Description.OperationDescription.Behaviors%2A>.|  
  
|Valeur MessageContractAttribute|Valeur de l’arborescence de description affectée|  
|------------------------------------|-------------------------------------|  
|ProtectionLevel|<xref:System.ServiceModel.Description.MessageDescription.ProtectionLevel%2A>|  
|WrapperName|<xref:System.ServiceModel.Description.MessageBodyDescription.WrapperName%2A>|  
|WrapperNamespace|<xref:System.ServiceModel.Description.MessageBodyDescription.WrapperNamespace%2A>|  
  
|Valeur MessageHeaderAttribute|Valeur de l’arborescence de description affectée|  
|----------------------------------|-------------------------------------|  
|Acteur|<xref:System.ServiceModel.Description.MessageHeaderDescription.Actor%2A>pour l’en-tête correspondant dans<xref:System.ServiceModel.Description.MessageDescription.Headers%2A>|  
|MustUnderstand|<xref:System.ServiceModel.Description.MessageHeaderDescription.MustUnderstand%2A>pour l’en-tête correspondant dans<xref:System.ServiceModel.Description.MessageDescription.Headers%2A>|  
|Name|<xref:System.ServiceModel.Description.MessagePartDescription.Name%2A>pour l’en-tête correspondant dans<xref:System.ServiceModel.Description.MessageDescription.Headers%2A>|  
|Espace de noms|<xref:System.ServiceModel.Description.MessagePartDescription.Namespace%2A>pour l’en-tête correspondant dans<xref:System.ServiceModel.Description.MessageDescription.Headers%2A>|  
|ProtectionLevel|<xref:System.ServiceModel.Description.MessagePartDescription.ProtectionLevel%2A>pour l’en-tête correspondant dans<xref:System.ServiceModel.Description.MessageDescription.Headers%2A>|  
|Relay|<xref:System.ServiceModel.Description.MessageHeaderDescription.Relay%2A>pour l’en-tête correspondant dans<xref:System.ServiceModel.Description.MessageDescription.Headers%2A>|  
  
|Valeur MessageBodyMemberAttribute|Valeur de l’arborescence de description affectée|  
|--------------------------------------|-------------------------------------|  
|Name|<xref:System.ServiceModel.Description.MessagePartDescription.Name%2A>pour la partie correspondante dans<xref:System.ServiceModel.Description.MessageBodyDescription.Parts%2A>|  
|Espace de noms|<xref:System.ServiceModel.Description.MessagePartDescription.Namespace%2A>pour la partie correspondante dans<xref:System.ServiceModel.Description.MessageBodyDescription.Parts%2A>|  
|Trier|<xref:System.ServiceModel.Description.MessagePartDescription.Index%2A>pour la partie correspondante dans<xref:System.ServiceModel.Description.MessageBodyDescription.Parts%2A>|  
|ProtectionLevel|<xref:System.ServiceModel.Description.MessagePartDescription.ProtectionLevel%2A>pour la partie correspondante dans<xref:System.ServiceModel.Description.MessageBodyDescription.Parts%2A>|  
  
|Valeur MessageHeaderArrayAttribute|Valeur de l’arborescence de description affectée|  
|---------------------------------------|-------------------------------------|  
|Acteur|<xref:System.ServiceModel.Description.MessageHeaderDescription.Actor%2A>|  
|MustUnderstand|<xref:System.ServiceModel.Description.MessageHeaderDescription.MustUnderstand%2A>|  
|Name|<xref:System.ServiceModel.Description.MessagePartDescription.Name%2A>|  
|Espace de noms|<xref:System.ServiceModel.Description.MessagePartDescription.Namespace%2A>|  
|ProtectionLevel|<xref:System.ServiceModel.Description.MessagePartDescription.ProtectionLevel%2A>|  
|Relay|<xref:System.ServiceModel.Description.MessageHeaderDescription.Relay%2A>|  
  
|Valeur MessagePropertyAttribute|Valeur de l’arborescence de description affectée|  
|------------------------------------|-------------------------------------|  
|Name|<xref:System.ServiceModel.Description.MessagePartDescription.Name%2A>|  
  
|Valeur MessageParameterAttribute|Valeur de l’arborescence de description affectée|  
|-------------------------------------|-------------------------------------|  
|Name|<xref:System.ServiceModel.Description.MessagePartDescription.Name%2A>pour la partie correspondante dans<xref:System.ServiceModel.Description.MessageBodyDescription.Parts%2A>|  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]manière dont les valeurs d’arborescence de description sont converties dans les métadonnées, consultez [ServiceDescription et WSDL référence](../../../../docs/framework/wcf/feature-details/servicedescription-and-wsdl-reference.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur ServiceDescription et WSDL](../../../../docs/framework/wcf/feature-details/servicedescription-and-wsdl-reference.md)
