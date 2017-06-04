---
title: "Valeurs par d&#233;faut des membres de donn&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "membres de données (WCF)"
  - "membres de données (WCF), valeurs par défaut"
ms.assetid: 53a3b505-4b27-444b-b079-0eb84a97cfd8
caps.latest.revision: 10
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 10
---
# Valeurs par d&#233;faut des membres de donn&#233;es
Dans [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], les types possèdent un concept de *valeurs par défaut*.Ainsi, la valeur par défaut d'un type référence est `null`, et celle d'un type entier est zéro.Il est parfois préférable d'omettre un membre de données des données sérialisées lorsqu'il est défini à sa valeur par défaut.Le membre ayant une valeur par défaut, il n'est pas nécessaire de sérialiser une valeur réelle ; cela présente un avantage en termes de performance.  
  
 Pour omettre un membre des données sérialisées, affectez `false` à la propriété <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> de l'attribut <xref:System.Runtime.Serialization.DataMemberAttribute> \(la valeur par défaut est `true`\).  
  
> [!NOTE]
>  Vous devez uniquement affecter la valeur `false` à la propriété <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> en cas de besoin spécifique, par exemple à des fins d'interopérabilité ou pour réduire la taille des données.  
  
## Exemple  
 Le code suivant a plusieurs membres avec <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> défini à `false`.  
  
 [!code-csharp[DataMemberAttribute#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/datamemberattribute/cs/overview.cs#4)]
 [!code-vb[DataMemberAttribute#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/datamemberattribute/vb/overview.vb#4)]  
  
 Si une instance de cette classe est sérialisée, le résultat est le suivant : `employeeName` et `employeeID` sont sérialisés.La valeur null pour `employeeName` et la valeur zéro pour `employeeID` font explicitement partie des données sérialisées.Toutefois, les membres `position`, `salary` et `bonus` ne sont pas sérialisées.Enfin, `targetSalary` est sérialisé comme d'habitude, même si la propriété <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> a la valeur `false`, car 57800 ne correspond pas à la valeur .NET par défaut pour un entier, qui est zéro.  
  
### Représentation XML  
 Si l'exemple précédent est sérialisé en XML, la représentation est similaire à la suivante.  
  
```  
<Employee>  
   <employeeName xsi:nil="true" />  
   <employeeID>0</employeeID>  
<targetSalary>57800</targetSalary>  
</Employee>  
```  
  
 L'attribut `xsi:nil` est un attribut spécial dans l'espace de noms de l'instance WC3 \(World Wide Web Consortium \) XML Schema qui offre un moyen interopérable pour représenter explicitement une valeur null.Notez que le XML ne contient aucune information sur le poste, le salaire et les primes des membres de données.L'extrémité de réception peut les interpréter comme `null`, zéro et `null`, respectivement.Il n'y a aucune garantie qu'un désérialiseur tiers puisse effectuer correctement l'interprétation ; c'est pourquoi ce modèle n'est pas recommandé.La classe <xref:System.Runtime.Serialization.DataContractSerializer> sélectionne systématiquement l'interprétation correcte pour les valeurs manquantes.  
  
### Interaction avec IsRequired  
 Comme indiqué dans [Contrôle de version des contrats de données](../../../../docs/framework/wcf/feature-details/data-contract-versioning.md), l'attribut <xref:System.Runtime.Serialization.DataMemberAttribute> a une propriété <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> \(la valeur par défaut est `false`\).La propriété indique si un membre de données spécifique doit ou non être présent dans les données sérialisées lorsqu'il est désérialisé.Si `IsRequired` a la valeur `true` \(ce qui indique qu'une valeur doit être présente\) et que <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> a la valeur `false` \(ce qui indique que la valeur ne doit pas être présente si la valeur indiquée est celle par défaut\), les valeurs par défaut de ce membre de données ne peuvent pas être sérialisées car les résultats seraient contradictoires.Si un membre de données de ce type à pour valeur sa valeur par défaut \(généralement `null` ou zéro\) et qu'une sérialisation est tentée, une exception <xref:System.Runtime.Serialization.SerializationException> est levée.  
  
### Représentation de schéma  
 Les détails de la représentation de schéma XSD \(XML Schema Definition Language\) des membres de données lorsque la propriété `EmitDefaultValue` a la valeur `false` sont présentés dans [Référence des schémas de contrats de données](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md).Toutefois, en voici une brève vue d'ensemble :  
  
-   Lorsque <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> a la valeur `false`, il est représenté dans le schéma sous forme d'une annotation spécifique à [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].Il n'existe pas de moyen interopérable pour représenter ces informations.En particulier, l'attribut "default" dans le schéma n'est pas utilisé à cette fin, l'attribut `minOccurs` est uniquement affecté par le paramètre <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A>, et l'attribut `nillable` est uniquement affecté par le type du membre de données.  
  
-   La valeur par défaut réelle à utiliser n'est pas présente dans le schéma.C'est au point de terminaison de réception d'interpréter correctement un élément manquant.  
  
 Sur l'importation de schéma, la propriété <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> a automatiquement la valeur `false` chaque fois que l'annotation spécifique à [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] précédemment mentionnée est détectée.Elle a également la valeur `false` pour les types référence dont la propriété `nillable` a la valeur `false` afin de prendre en charge des scénarios d'interopérabilité spécifiques qui se produisent généralement lors de la consommation des services Web [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)].  
  
## Voir aussi  
 <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A>   
 <xref:System.Runtime.Serialization.DataMemberAttribute>