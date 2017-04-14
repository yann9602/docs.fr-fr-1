---
title: "Serialization1 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
ms.assetid: bebb27ac-9712-4196-9931-de19fc04dbac
caps.latest.revision: 4
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
---
# S&#233;rialisation
La sérialisation est le processus de conversion d’un objet dans un format qui peut être facilement persistante ou transporté. Par exemple, vous pouvez sérialiser un objet, le transfert via Internet à l’aide de HTTP et désérialisé à l’ordinateur de destination.  
  
 Le .NET Framework propose trois technologies principales de sérialisation optimisés pour différents scénarios de sérialisation. Le tableau suivant répertorie les principaux types d’infrastructure liés à ces technologies et ces technologies.  
  
|**Nom de la technologie**|**Types principaux**|**Scénarios**|  
|-------------------------------|--------------------------|-------------------|  
|**Sérialisation de contrat de données**|<xref:System.Runtime.Serialization.DataContractAttribute> <br /> <xref:System.Runtime.Serialization.DataMemberAttribute> <br /> <xref:System.Runtime.Serialization.DataContractSerializer> <br /> <xref:System.Runtime.Serialization.NetDataContractSerializer> <br /> <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> <br /> <xref:System.Runtime.Serialization.ISerializable>|Persistance générale<br />Services Web<br />JSON|  
|**Sérialisation XML**|<xref:System.Xml.Serialization.XmlSerializer>|Format XML avec un contrôle total sur la forme du XML|  
|**Sérialisation du runtime \(binaire et SOAP\)**|<xref:System.SerializableAttribute> <br /> <xref:System.Runtime.Serialization.ISerializable> <br /> <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> <br /> <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>|.NET Remoting|  
  
 **✓ faire** réflexion sur la sérialisation lorsque vous concevez de nouveaux types.  
  
## Choix de la technologie de sérialisation appropriés pour prendre en charge  
 **✓ envisagez** prise en charge de la sérialisation de contrat de données si les instances de votre type devront peut\-être être rendues persistantes ou utilisées dans les Services Web.  
  
 **✓ envisagez** prise en charge de la sérialisation XML à la place ou en plus de la sérialisation de contrat de données si vous avez besoin de davantage de contrôle sur le format XML qui est généré lorsque le type est sérialisé.  
  
 Cela peut être nécessaire dans certains interopérabilité construire des scénarios où vous devez utiliser un document XML non pris en charge par la sérialisation de contrat de données, par exemple, pour générer des attributs XML.  
  
 **✓ envisagez** prise en charge de la sérialisation du Runtime si des instances de votre type doivent se déplacer au\-delà des limites de .NET Remoting.  
  
 **X éviter** prise en charge de la sérialisation du Runtime ou la sérialisation XML pour des raisons de persistance. Préférez sérialisation de contrat de données à la place.  
  
## Sérialisation de contrat de données prise en charge  
 Types peuvent prendre en charge sérialisation de contrat de données en appliquant la <xref:System.Runtime.Serialization.DataContractAttribute> pour le type et le <xref:System.Runtime.Serialization.DataMemberAttribute> aux membres \(champs et propriétés\) du type.  
  
 **✓ envisagez** marquer les données membres de votre public de type si le type peut être utilisé avec une confiance partielle.  
  
 Avec une confiance totale, les sérialiseurs de contrat de données peuvent sérialiser et désérialiser des membres et types non publics, mais uniquement les membres publics pouvant être sérialisés et désérialisés en confiance partielle.  
  
 **✓ faire** implémenter un accesseur Get et l’accesseur Set sur toutes les propriétés qui ont <xref:System.Runtime.Serialization.DataMemberAttribute>. Les sérialiseurs de contrat de données nécessitent l’accesseur Get et Set pour que le type soit considéré comme sérialisable. \(Dans le .NET Framework 3.5 SP1, certaines propriétés de la collection peuvent être seule.\) Si le type n’est utilisé avec une confiance partielle, une ou deux des accesseurs de propriété peuvent être non publics.  
  
 **✓ envisagez** à l’aide de rappels de sérialisation pour l’initialisation des instances désérialisées.  
  
 Les constructeurs ne sont pas appelés lorsque les objets sont désérialisés. \(Il existe des exceptions à la règle. Constructeurs de collections est marquée avec <xref:System.Runtime.Serialization.CollectionDataContractAttribute> sont appelées pendant la désérialisation.\) Par conséquent, toute logique qui s’exécute pendant la construction normale doit être implémentée en tant qu’un des rappels de sérialisation.  
  
 `OnDeserializedAttribute` est l’attribut de rappel plus couramment utilisés. Les autres attributs de la famille sont <xref:System.Runtime.Serialization.OnDeserializingAttribute>,  <xref:System.Runtime.Serialization.OnSerializingAttribute>, et <xref:System.Runtime.Serialization.OnSerializedAttribute>. Ils permettent de marquer les rappels exécutés avant la désérialisation, avant la sérialisation et enfin, après la sérialisation, respectivement.  
  
 **✓ envisagez** à l’aide de la <xref:System.Runtime.Serialization.KnownTypeAttribute> pour indiquer les types concrets qui doivent être utilisés lors de la désérialisation d’un graphique d’objet complexe.  
  
 **✓ faire** prendre en compte la compatibilité ascendante et descendante lors de la création ou la modification des types sérialisables.  
  
 N’oubliez pas que les flux sérialisés de futures versions de votre type peut être désérialisé dans la version actuelle du type et vice versa.  
  
 Assurez\-vous que vous comprenez que les membres de données, même privées et internes, ne peuvent pas changer leurs noms, types ou même leur ordre dans les futures versions du type sauf si, veillez à conserver le contrat à l’aide de paramètres explicites pour les attributs de contrat de données.  
  
 Tester la compatibilité de sérialisation lorsque des modifications apportées aux types sérialisables. Essayez de désérialiser la nouvelle version dans une ancienne version et vice versa.  
  
 **✓ envisagez** l’implémentation <xref:System.Runtime.Serialization.IExtensibleDataObject> pour permettre l’aller\-retour entre les différentes versions du type.  
  
 L’interface permet au sérialiseur de garantir qu’aucune donnée n’est perdue lors de l’aller\-retour. Le <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A?displayProperty=fullName> propriété est utilisée pour stocker des données à partir de la version futures du type qui est inconnu de la version actuelle, et par conséquent, il ne peut pas stocker dans ses données membres. Lorsque la version actuelle est ensuite sérialisée et désérialisée dans une version ultérieure, les données supplémentaires seront disponibles dans le flux sérialisé.  
  
## Prise en charge de la sérialisation XML  
 Sérialisation de contrat de données est la principale \(par défaut\) technologie de sérialisation dans le .NET Framework, mais il existe des scénarios de sérialisation qui ne gère pas la sérialisation de contrat de données. Par exemple, il ne vous accorde pas un contrôle total sur la forme du XML généré ou consommé par le sérialiseur. Si ce contrôle renforcé est nécessaire, la sérialisation XML doit être utilisée, et vous devez concevoir vos types pour prendre en charge cette technologie de sérialisation.  
  
 **X éviter** concevoir vos types spécifiquement pour la sérialisation XML, sauf si vous avez une bonne raison pour contrôler la forme du XML généré. Cette technologie de sérialisation a été remplacée par la sérialisation de contrat de données indiqué dans la section précédente.  
  
 **✓ envisagez** implémentant le <xref:System.Xml.Serialization.IXmlSerializable> interface si vous souhaitez contrôler davantage la forme du XML sérialisé que celui proposé en appliquant les attributs de sérialisation XML. Deux méthodes de l’interface, <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> et <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A>, vous permettent de contrôler entièrement le flux XML sérialisé. Vous pouvez également contrôler le schéma XML qui est généré pour le type en appliquant la `XmlSchemaProviderAttribute`.  
  
## Prise en charge de la sérialisation du Runtime  
 Sérialisation du runtime est une technologie utilisée par .NET Remoting. Si vous pensez que vos types vont être transportés à l’aide de .NET Remoting, vous devez vous assurer qu’ils prennent en charge la sérialisation du Runtime.  
  
 La prise en charge de base pour la sérialisation du Runtime peut être fourni en appliquant la <xref:System.SerializableAttribute>, et des scénarios plus avancés impliquent l’implémentation d’un simple modèle sérialisable du Runtime \(implémenter <xref:System.Runtime.Serialization.ISerializable> et fournissent le constructeur de sérialisation\).  
  
 **✓ envisagez** prise en charge de la sérialisation du Runtime si vos types sont utilisés avec .NET Remoting. Par exemple, le <xref:System.AddIn?displayProperty=fullName> espace de noms utilise .NET Remoting, et par conséquent, tous les types échangent entre `System.AddIn` les compléments doivent prendre en charge de la sérialisation du Runtime.  
  
 **✓ envisagez** l’implémentation du modèle sérialisable du Runtime si vous souhaitez contrôler le processus de sérialisation. Par exemple, si vous souhaitez transformer les données en tant qu’elle obtient sérialisée ou désérialisée.  
  
 Le modèle est très simple. Vous devez faire est implémenter le <xref:System.Runtime.Serialization.ISerializable> de l’interface et de fournir un constructeur spécial qui est utilisé lorsque l’objet est désérialisé.  
  
 **✓ faire** Protégez le constructeur de sérialisation et fournissez deux paramètres typés et nommés exactement comme indiqué dans l’exemple ici.  
  
```  
[Serializable]  
public class Person : ISerializable {  
    protected Person(SerializationInfo info, StreamingContext context) {  
        ...  
    }  
}  
```  
  
 **✓ faire** implémenter le `ISerializable` membres explicitement.  
  
 **✓ faire** s’appliquent à une demande de liaison <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> mise en œuvre. Cela garantit qu’approuvée uniquement entièrement core et le sérialiseur du Runtime ont accès au membre.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*  
  
 *Réimprimé avec l’autorisation de Pearson éducation, Inc. à partir de [Framework Design Guidelines : Conventions, langages et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison\-Wesley Professional dans le cadre de la série de développement de Microsoft Windows.*  
  
## Voir aussi  
 [Instructions de conception d’infrastructure](../../../docs/standard/design-guidelines/index.md)   
 [Indications relatives à l'utilisation](../../../docs/standard/design-guidelines/usage-guidelines.md)