---
title: "x:Reference Markup Extension | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "x:Reference markup extension [XAML Services]"
  - "XAML [XAML Services], x:Reference Markup Extension"
  - "Reference markup extension [XAML Services]"
ms.assetid: 2982e68b-d26b-4aa3-826a-34c57a9c5199
caps.latest.revision: 8
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
caps.handback.revision: 8
---
# x:Reference Markup Extension
Référence une instance déclarée ailleurs dans le balisage XAML.  La référence renvoie au `x:Name` d'un élément.  
  
## Utilisation d'attributs XAML  
  
```  
<object property="{x:Reference instancexName}" .../>  
```  
  
## Utilisation d'éléments objet XAML  
  
```  
<object>  
  <object.property>  
    <x:Reference Name="instancexName"/>  
  </object.property>  
</object>  
```  
  
## Valeurs XAML  
  
|||  
|-|-|  
|`instancexName`|Valeur `x:Name` \(ou valeur de la propriété identifiée par <xref:System.Windows.Markup.RuntimeNamePropertyAttribute> de l'instance référencée.|  
  
## Notes  
 `x:Reference` fournit la prise en charge de niveau de langage XAML pour un concept de référence d'élément qui a été implémenté dans des frameworks spécifiques, tels que WPF.  
  
## x:Reference et WPF  
 Dans WPF et XAML 2006, les références d'éléments sont adressées par la fonctionnalité au niveau de l'infrastructure de la liaison <xref:System.Windows.Data.Binding.ElementName%2A>.  Pour la plupart des applications WPF et scénarios, la liaison <xref:System.Windows.Data.Binding.ElementName%2A> doit encore être utilisée.  Les exceptions à cette recommandation générale peuvent inclure des cas où il y a du contexte de données ou d'autres considérations sur la définition du périmètre qui rendent la liaison de données irréaliste, et où la compilation du balisage n'est pas impliquée.  
  
 `x:Reference` est une construction définie dans XAML 2009.  Dans WPF, vous pouvez utiliser des fonctionnalités XAML 2009, mais uniquement pour XAML qui n'est pas compilé par balise WPF.  XAML compilé par balise et le formulaire BAML de XAML ne prennent pas en charge actuellement les mots clés de langage XAML 2009 et les fonctionnalités.