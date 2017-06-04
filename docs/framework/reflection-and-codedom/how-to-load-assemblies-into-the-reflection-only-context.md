---
title: "Comment&#160;: charger des assemblys dans le contexte de r&#233;flexion uniquement | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "assemblys (.NET Framework), charger pour la réflexion"
  - "assemblys (.NET Framework), contexte de chargeur de réflexion uniquement"
  - "attributs (.NET Framework), récupérer"
  - "réflexion, contexte de chargeur de réflexion uniquement"
  - "contexte de chargeur de réflexion uniquement"
ms.assetid: 9818b660-52f5-423d-a9af-e75163aa7068
caps.latest.revision: 8
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 8
---
# Comment&#160;: charger des assemblys dans le contexte de r&#233;flexion uniquement
Le contexte de chargement de réflexion uniquement permet d'examiner des assemblys compilés pour d'autres plateformes ou d'autres versions du .NET Framework.  Le code chargé dans ce contexte peut uniquement être examiné ; il ne peut pas être exécuté.  Cela signifie qu'il est impossible de créer des objets car les constructeurs ne peuvent pas être exécutés.  Puisque le code ne peut pas être exécuté, les dépendances ne sont pas chargées automatiquement.  Si vous devez les examiner, vous devez les charger vous\-même.  
  
### Pour charger un assembly dans le contexte de chargement de réflexion uniquement  
  
1.  Utilisez la méthode surchargée <xref:System.Reflection.Assembly.ReflectionOnlyLoad%28System.String%29> pour charger l'assembly avec son nom complet ou la méthode <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> pour charger l'assembly avec son chemin d'accès.  Si l'assembly est une image binaire, utilisez la méthode surchargée [ReflectionOnlyLoad\(Byte\<xref:System.Reflection.Assembly.ReflectionOnlyLoad%28System.Byte%5B%5D%29>.  
  
    > [!NOTE]
    >  Vous ne pouvez pas utiliser le contexte de réflexion uniquement pour charger une version de mscorlib.dll à partir d'une version du .NET Framework autre que la version dans le contexte d'exécution.  
  
2.  Si l'assembly possède des dépendances, la méthode <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A> ne les charge pas.  Si vous devez les examiner, vous devez les charger vous\-même.  
  
3.  Déterminez si un assembly est chargé dans le contexte de réflexion uniquement en utilisant la propriété <xref:System.Reflection.Assembly.ReflectionOnly%2A> de l'assembly.  
  
4.  Si des attributs ont été appliqués à l'assembly ou à des types de l'assembly, examinez ces attributs en utilisant la classe <xref:System.Reflection.CustomAttributeData> pour éviter toute tentative d'exécution du code dans le contexte de réflexion uniquement.  Utilisez la surcharge appropriée de la méthode <xref:System.Reflection.CustomAttributeData.GetCustomAttributes%2A?displayProperty=fullName> pour obtenir des objets <xref:System.Reflection.CustomAttributeData> qui représentent les attributs appliqués à un assembly, un membre, un module ou un paramètre.  
  
    > [!NOTE]
    >  Les attributs appliqués à l'assembly ou à son contenu peuvent être définis dans l'assembly ou dans un autre assembly chargé dans le contexte de réflexion uniquement.  Il n'existe aucun moyen de déterminer à l'avance l'emplacement dans lequel les attributs sont définis.  
  
## Exemple  
 L'exemple de code suivant montre comment examiner les attributs appliqués à un assembly chargé dans le contexte de réflexion uniquement.  
  
 L'exemple de code suivant définit un attribut personnalisé avec deux constructeurs et une propriété.  L'attribut est appliqué à l'assembly, à un type déclaré dans l'assembly, à une méthode du type et à un paramètre de la méthode.  Lorsqu'il est exécuté, l'assembly se charge dans le contexte de réflexion uniquement et affiche des informations sur les attributs personnalisés qui lui ont été appliqués ainsi qu'aux types et membres qu'il contient.  
  
> [!NOTE]
>  Pour simplifier l'exemple de code, l'assembly se charge et s'examine lui\-même.  Normalement, il est inhabituel de trouver le même assembly chargé à la fois dans le contexte d'exécution et le contexte de réflexion uniquement.  
  
 [!code-cpp[CustomAttributeData#1](../../../samples/snippets/cpp/VS_Snippets_CLR/CustomAttributeData/CPP/source.cpp#1)]
 [!code-csharp[CustomAttributeData#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CustomAttributeData/CS/source.cs#1)]
 [!code-vb[CustomAttributeData#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CustomAttributeData/VB/source.vb#1)]  
  
## Voir aussi  
 <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A>   
 <xref:System.Reflection.Assembly.ReflectionOnly%2A>   
 <xref:System.Reflection.CustomAttributeData>