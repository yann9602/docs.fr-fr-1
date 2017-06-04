---
title: "S&#233;rialisation s&#233;lective | Microsoft Docs"
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
  - "sérialisation binaire, sérialisation sélective"
  - "sérialisation, sérialisation sélective"
ms.assetid: 39c56635-95d2-4afd-aff1-b022e7649bb3
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# S&#233;rialisation s&#233;lective
Une classe contient souvent des champs qui ne doivent pas être sérialisés.Par exemple, supposez qu'une classe stocke un ID de thread dans une variable membre.Lorsque la classe est désérialisée, il se peut que le thread stocké pour l'ID au moment de la sérialisation de la classe ne s'exécute plus ; la sérialisation de cette valeur est donc inutile.Vous pouvez empêcher des variables membres d'être sérialisées en les marquant avec l'attribut [NonSerialized](frlrfSystemNonSerializedAttributeClassTopic) comme suit.  
  
```csharp  
[Serializable]  
public class MyObject   
{  
  public int n1;  
  [NonSerialized] public int n2;  
  public String str;  
}  
```  
  
 Si possible, faites en sorte qu'un objet pouvant contenir des données de sécurité sensibles soit non sérialisable.Si l'objet doit être sérialisé, appliquez l'attribut **NonSerialized** aux champs spécifiques qui stockent des données sensibles.Si vous n'excluez pas ces champs de la sérialisation, notez que les données qu'ils stockent seront exposées à tout code autorisé à sérialiser.Pour plus d'informations sur l'écriture du code de sérialisation sécurisé, consultez [Sécurité et sérialisation](../../../docs/framework/misc/security-and-serialization.md).  
  
## Voir aussi  
 [Sérialisation binaire](../../../docs/framework/serialization/binary-serialization.md)   
 [Remote Objects](http://msdn.microsoft.com/fr-fr/515686e6-0a8d-42f7-8188-73abede57c58)   
 [Sérialisation XML et SOAP](../../../docs/framework/serialization/xml-and-soap-serialization.md)   
 [Sécurité et sérialisation](../../../docs/framework/misc/security-and-serialization.md)