---
title: "&#201;l&#233;ment &lt;xmlSerializer&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "élément <xmlSerializer>"
  - "sérialisation XML, configuration"
  - "xmlSerializer (élément)"
ms.assetid: d129d10c-3eb7-45d9-8098-5fa853825e47
caps.latest.revision: 4
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# &#201;l&#233;ment &lt;xmlSerializer&gt;
Spécifie si un contrôle supplémentaire de la progression de <xref:System.Xml.Serialization.XmlSerializer> est effectué.  
  
## Syntaxe  
  
```  
  
<xmlSerializer checkDeserializerAdvance = "true"|"false" />  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|**checkDeserializeAdvances**|Spécifie si la progression de <xref:System.Xml.Serialization.XmlSerializer> est vérifiée.  Affectez "true" ou "false" à l'attribut.  La valeur par défaut est "true".|  
|**useLegacySerializationGeneration**|Spécifie si <xref:System.Xml.Serialization.XmlSerializer> utilise la génération de sérialisation héritée qui génère des assemblys en écrivant le code C\# dans un fichier, puis en le compilant dans un assembly.  La valeur par défaut est **false**.|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[Élément \<system.xml.serialization\>](../../../docs/framework/serialization/system-xml-serialization-element.md)|Contient des paramètres de configuration pour les classes <xref:System.Xml.Serialization.XmlSerializer> et <xref:System.Xml.Serialization.XmlSchemaImporter>.|  
  
## Notes  
 Par défaut, le <xref:System.Xml.Serialization.XmlSerializer> fournit une couche supplémentaire de sécurité contre des attaques par déni de service potentielles lors de la désérialisation de données non fiables.  Pour ce faire, il tente de détecter des boucles infinies pendant la désérialisation.  Si une telle condition est détectée, une exception est levée avec le message suivant : « Erreur interne : la désérialisation n'a pas pu avancer sur le flux de données sous\-jacent. »  
  
 Le fait de recevoir ce message n'indique pas nécessairement qu'une attaque par déni de service est en cours.  Dans de rares circonstances, le mécanisme de détection de boucles infinies génère un faux positif et l'exception est levée pour un message entrant légitime.  Si vous détectez, dans votre application particulière, que des messages légitimes sont rejetés par cette couche de protection supplémentaire, affectez "false" à l'attribut **checkDeserializeAdvances**.  
  
## Exemple  
 L'exemple de code suivant affecte "false" à l'attribut **checkDeserializeAdvances**.  
  
```  
<configuration>  
  <system.xml.serialization>  
    <xmlSerializer checkDeserializeAdvances="false" />  
  </system.xml.serialization>  
</configuration>  
```  
  
## Voir aussi  
 <xref:System.Xml.Serialization.XmlSerializer>   
 [Élément \<system.xml.serialization\>](../../../docs/framework/serialization/system-xml-serialization-element.md)   
 [Sérialisation XML et SOAP](../../../docs/framework/serialization/xml-and-soap-serialization.md)