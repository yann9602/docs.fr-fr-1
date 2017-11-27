---
title: Serialization1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bebb27ac-9712-4196-9931-de19fc04dbac
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e63428400a7868b71a2d8e52637e4b22e4c44ee7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="serialization"></a>Sérialisation
La sérialisation est le processus de conversion d’un objet dans un format qui peut être facilement persistante ou transporté. Par exemple, vous pouvez sérialiser un objet, il transport via Internet à l’aide de HTTP et il désérialisée à l’ordinateur de destination.  
  
 Le .NET Framework propose trois technologies de sérialisation principal optimisés pour différents scénarios de sérialisation. Le tableau suivant répertorie ces technologies et les principaux types Framework qui leur sont associés.  
  
|**Nom de technologie**|**Types principaux**|**Scénarios**|  
|-------------------------|--------------------|-------------------|  
|**Sérialisation de contrat de données**|<xref:System.Runtime.Serialization.DataContractAttribute> <br /> <xref:System.Runtime.Serialization.DataMemberAttribute> <br /> <xref:System.Runtime.Serialization.DataContractSerializer> <br /> <xref:System.Runtime.Serialization.NetDataContractSerializer> <br /> <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> <br /> <xref:System.Runtime.Serialization.ISerializable>|Persistance générale<br />Services Web<br />JSON|  
|**Sérialisation XML**|<xref:System.Xml.Serialization.XmlSerializer>|Format XML avec un contrôle total sur la forme du code XML|  
|**Sérialisation du runtime (binaire et SOAP)**|<xref:System.SerializableAttribute> <br /> <xref:System.Runtime.Serialization.ISerializable> <br /> <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> <br /> <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>|.NET Remoting|  
  
 **✓ FAIRE** réflexion sur la sérialisation lors de la création de nouveaux types.  
  
## <a name="choosing-the-right-serialization-technology-to-support"></a>Sélection de la technologie de sérialisation appropriée à prendre en charge  
 **✓ Envisagez** prenant en charge la sérialisation de contrat de données si les instances de votre type peuvent doivent être rendues persistantes ou sont utilisés dans les Services Web.  
  
 **✓ Envisagez** prenant en charge la sérialisation XML à la place ou en plus de la sérialisation de contrat de données si vous avez besoin de davantage de contrôle sur le format XML qui se produit quand le type est sérialisé.  
  
 Cela peut être nécessaire dans certains interopérabilité construire des scénarios où vous devez utiliser un code XML non pris en charge par la sérialisation de contrat de données, par exemple, pour produire des attributs XML.  
  
 **✓ Envisagez** prenant en charge la sérialisation de l’exécution si les instances de ce type doivent circuler dans les limites de .NET Remoting.  
  
 **X Évitez** prenant en charge la sérialisation du Runtime ou la sérialisation XML uniquement pour des raisons de persistance générales. Préférez la sérialisation de contrat de données à la place.  
  
## <a name="supporting-data-contract-serialization"></a>Prise en charge de la sérialisation du contrat de données  
 Types peuvent prendre en charge sérialisation de contrat de données en appliquant la <xref:System.Runtime.Serialization.DataContractAttribute> pour le type et le <xref:System.Runtime.Serialization.DataMemberAttribute> aux membres (champs et propriétés) du type.  
  
 **✓ Envisagez** marquant les membres de données de votre type public si le type peut être utilisé avec une confiance partielle.  
  
 En mode confiance totale, les sérialiseurs de contrat de données peuvent sérialiser et désérialiser des types non publics et les membres, mais seuls les membres publics pouvant être sérialisés et désérialisés en confiance partielle.  
  
 **✓ FAIRE** implémenter un accesseur Get et un accesseur Set pour toutes les propriétés qui ont <xref:System.Runtime.Serialization.DataMemberAttribute>. Sérialiseurs de contrat de données nécessitent l’accesseur Get et l’accesseur Set pour le type soit considérée comme sérialisable. (Dans le .NET Framework 3.5 SP1, certaines propriétés de collection peuvent être get uniquement.) Si le type n'est pas utilisé en mode de confiance partielle, un des accesseurs de propriété, ou les deux, peuvent être non publics.  
  
 **✓ Envisagez** à l’aide de l’initialisation d’instances désérialisées les rappels de sérialisation.  
  
 Les constructeurs ne sont pas appelés lorsque les objets sont désérialisés. (Il existe des exceptions à la règle. Constructeurs de collections est marquée avec <xref:System.Runtime.Serialization.CollectionDataContractAttribute> sont appelées pendant la désérialisation.) Par conséquent, toute logique qui s’exécute pendant la construction normale doit être implémentée en tant qu’un des rappels de sérialisation.  
  
 `OnDeserializedAttribute`est l’attribut de rappel couramment utilisées. Les autres attributs de la famille sont <xref:System.Runtime.Serialization.OnDeserializingAttribute>,  <xref:System.Runtime.Serialization.OnSerializingAttribute> et <xref:System.Runtime.Serialization.OnSerializedAttribute>. Ils peuvent être utilisés pour marquer les rappels exécutés avant la désérialisation, avant la sérialisation et enfin, après la sérialisation, respectivement.  
  
 **✓ Envisagez** à l’aide de la <xref:System.Runtime.Serialization.KnownTypeAttribute> pour indiquer les types concrets qui doivent être utilisées lors de la désérialisation d’un graphique d’objets complexes.  
  
 **✓ FAIRE** prendre en compte la compatibilité ascendante et descendante lors de la création ou la modification des types sérialisables.  
  
 Gardez à l'esprit que les flux sérialisés de futures versions de votre type peuvent être désérialisés dans la version actuelle du type, et inversement.  
  
 Assurez-vous que vous comprenez que les membres de données, même privées et internes, ne peut pas changer leurs noms, types ou même leur commande dans les versions futures du type, sauf si une attention particulière est nécessaire pour conserver le contrat à l’aide de paramètres explicites pour les attributs de contrat de données .  
  
 Tester la compatibilité de la sérialisation lorsque des modifications apportées à des types sérialisables. Essayez de désérialiser la nouvelle version dans une ancienne version, et inversement.  
  
 **✓ Envisagez** implémentation <xref:System.Runtime.Serialization.IExtensibleDataObject> pour permettre l’aller-retour entre les différentes versions du type.  
  
 L'interface permet au sérialiseur de garantir qu'aucune donnée n'est perdue lors de l'aller-retour. Le <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A?displayProperty=nameWithType> propriété est utilisée pour stocker des données à partir de la prochaine version du type est inconnu dans la version actuelle, et par conséquent, il ne peut pas stocker dans ses membres de données. Lorsque la version actuelle est par la suite sérialisée et désérialisée dans une version ultérieure, les données supplémentaires seront disponibles dans le flux sérialisé.  
  
## <a name="supporting-xml-serialization"></a>Prise en charge de la sérialisation XML  
 Sérialisation de contrat de données est le principal (par défaut) technologie de sérialisation dans le .NET Framework, mais il existe des scénarios de sérialisation sérialisation de contrat de données ne prend pas en charge. Par exemple, vous n'avez pas le contrôle total sur la forme du XML généré ou consommé par le sérialiseur. Si un contrôle précis est nécessaire, la sérialisation XML doit être utilisée, et vous devez concevoir vos types pour prendre en charge cette technologie de sérialisation.  
  
 **X Évitez** vous concevez vos types spécifiquement pour la sérialisation XML, sauf si vous avez une raison très forte pour contrôler la forme du code XML généré. Cette technologie de sérialisation a été remplacée par la sérialisation du contrat de données présentée dans la section précédente.  
  
 **✓ Envisagez** implémentant le <xref:System.Xml.Serialization.IXmlSerializable> interface si vous souhaitez contrôler davantage la forme du code XML sérialisé que celle fournie en appliquant les attributs de sérialisation XML. Deux méthodes de l’interface, <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> et <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A>, vous permettent de contrôler entièrement le flux XML sérialisé. Vous pouvez également contrôler le schéma XML généré pour le type en appliquant la `XmlSchemaProviderAttribute`.  
  
## <a name="supporting-runtime-serialization"></a>Prise en charge de la sérialisation du runtime  
 Sérialisation du runtime est une technologie utilisée par le .NET Remoting. Si vous pensez que vos types seront transportés à l’aide de .NET Remoting, vous devez vous assurer qu’ils prennent en charge la sérialisation du Runtime.  
  
 La prise en charge de base pour la sérialisation du Runtime peut être fourni en appliquant la <xref:System.SerializableAttribute>, et des scénarios plus avancés impliquent l’implémentation d’un modèle sérialisable Runtime simple (implémenter <xref:System.Runtime.Serialization.ISerializable> et fournir le constructeur de sérialisation).  
  
 **✓ Envisagez** prenant en charge la sérialisation du Runtime si vos types seront utilisées avec la communication à distance .NET. Par exemple, le <xref:System.AddIn?displayProperty=nameWithType> espace de noms utilise .NET Remoting, et par conséquent, tous les types échangent entre `System.AddIn` compléments doivent prendre en charge de la sérialisation du Runtime.  
  
 **✓ Envisagez** implémentant le modèle sérialisable Runtime si vous souhaitez contrôler le processus de sérialisation. Par exemple, si vous souhaitez transformer des données à mesure qu'elles sont sérialisées ou désérialisées.  
  
 Le modèle est très simple. Il suffit d'implémenter l'interface <xref:System.Runtime.Serialization.ISerializable> et de fournir un constructeur spécial qui est utilisé lorsque l'objet est désérialisé.  
  
 **✓ FAIRE** Protégez le constructeur de sérialisation et de fournir les deux paramètres typés et nommés exactement comme indiqué dans l’exemple ici.  
  
```  
[Serializable]  
public class Person : ISerializable {  
    protected Person(SerializationInfo info, StreamingContext context) {  
        ...  
    }  
}  
```  
  
 **✓ FAIRE** implémenter le `ISerializable` membres explicitement.  
  
 **✓ FAIRE** s’appliquent à une demande de liaison <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=nameWithType> implémentation. Cela garantit qu’approuvé uniquement entièrement core et le sérialiseur de Runtime ont accès au membre.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*  
  
 *Réimprimées avec l’autorisation de Pearson éducation, Inc. à partir de [règles de conception d’infrastructure : Conventions, idiomes et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série de développement Microsoft Windows.*  
  
## <a name="see-also"></a>Voir aussi  
 [Règles de conception de .NET Framework](../../../docs/standard/design-guidelines/index.md)  
 [Instructions d’utilisation](../../../docs/standard/design-guidelines/usage-guidelines.md)
