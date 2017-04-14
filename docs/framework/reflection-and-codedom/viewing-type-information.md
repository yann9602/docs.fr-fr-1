---
title: "Affichage des informations de type | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "réflexion, afficher des informations de type"
  - "Type (objet)"
  - "types, afficher des informations de type"
  - "afficher des informations de type"
ms.assetid: 7e7303a9-4064-4738-b4e7-b75974ed70d2
caps.latest.revision: 13
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 12
---
# Affichage des informations de type
La classe <xref:System.Type?displayProperty=fullName> est l'élément central de la réflexion.  Le Common Language Runtime crée **Type** pour un type chargé, lorsque la réflexion le demande.  Vous pouvez utiliser les méthodes, champs, propriétés et classes imbriquées d'un objet **Type** pour connaître toutes les informations relatives à ce type.  
  
 Utilisez <xref:System.Reflection.Assembly.GetType%2A?displayProperty=fullName> ou <xref:System.Reflection.Assembly.GetTypes%2A?displayProperty=fullName> pour obtenir les objets **Type** des assemblys n'ayant pas été chargés, en passant le nom des types souhaités.  Utilisez <xref:System.Type.GetType%2A?displayProperty=fullName> pour obtenir les objets **Type** d'un assembly déjà chargé.  Utilisez <xref:System.Reflection.Module.GetType%2A?displayProperty=fullName> et <xref:System.Reflection.Module.GetTypes%2A?displayProperty=fullName> pour obtenir des objets de module **Type**.  
  
> [!NOTE]
>  Si vous souhaitez examiner et manipuler des types et des méthodes génériques, consultez les informations supplémentaires fournies dans [Réflexion et types génériques](../../../docs/framework/reflection-and-codedom/reflection-and-generic-types.md) et [Comment : examiner et instancier des types génériques avec la réflexion](../../../docs/framework/reflection-and-codedom/how-to-examine-and-instantiate-generic-types-with-reflection.md).  
  
 L'exemple suivant montre la syntaxe nécessaire pour obtenir l'objet <xref:System.Reflection.Assembly> et le module d'un assembly.  
  
 [!code-cpp[Conceptual.Types.ViewInfo#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source5.cpp#6)]
 [!code-csharp[Conceptual.Types.ViewInfo#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source5.cs#6)]
 [!code-vb[Conceptual.Types.ViewInfo#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source5.vb#6)]  
  
 L'exemple suivant montre comment obtenir des objets **Type** à partir d'un assembly chargé.  
  
 [!code-cpp[Conceptual.Types.ViewInfo#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source5.cpp#7)]
 [!code-csharp[Conceptual.Types.ViewInfo#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source5.cs#7)]
 [!code-vb[Conceptual.Types.ViewInfo#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source5.vb#7)]  
  
 Une fois **Type** obtenu, il existe de nombreuses façons de découvrir les informations relatives aux membres de ce type.  Par exemple, vous pouvez rechercher des informations sur tous les membres du type en appelant la méthode <xref:System.Type.GetMembers%2A?displayProperty=fullName>, qui obtient un tableau d'objets <xref:System.Reflection.MemberInfo> décrivant chaque membre du type en cours.  
  
 Vous pouvez également utiliser des méthodes sur la classe **Type** pour récupérer des informations sur les constructeurs, méthodes, événements, champs ou propriétés que vous spécifiez par le nom.  Par exemple, <xref:System.Type.GetConstructor%2A?displayProperty=fullName> encapsule un constructeur spécifique de la classe en cours.  
  
 Si vous disposez de **Type**, vous pouvez utiliser la propriété <xref:System.Type.Module%2A?displayProperty=fullName> pour obtenir un objet qui encapsule le module contenant ce type.  Utilisez la propriété <xref:System.Reflection.Module.Assembly%2A?displayProperty=fullName> pour localiser un objet qui encapsule l'assembly contenant le module.  Vous pouvez obtenir directement l'assembly qui encapsule le type en utilisant la propriété <xref:System.Type.Assembly%2A?displayProperty=fullName>.  
  
## System.Type et ConstructorInfo  
 L'exemple suivant montre comment répertorier les constructeurs d'une classe, dans le cas présent, la classe <xref:System.String>.  
  
 [!code-cpp[Conceptual.Types.ViewInfo#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source1.cpp#1)]
 [!code-csharp[Conceptual.Types.ViewInfo#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source1.cs#1)]
 [!code-vb[Conceptual.Types.ViewInfo#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source1.vb#1)]  
  
## MemberInfo, MethodInfo, FieldInfo et PropertyInfo  
 Obtenez des informations à propos des méthodes du type, propriétés, événements et champs à l'aide de <xref:System.Reflection.MemberInfo>, <xref:System.Reflection.MethodInfo>, <xref:System.Reflection.FieldInfo>ou objets <xref:System.Reflection.PropertyInfo>.  
  
 L'exemple suivant utilise **MemberInfo** pour répertorier le nombre de membres de la classe **System.IO.File** et utilise la propriété [System.Type.IsPublic](frlrfSystemTypeClassIsPublicTopic) pour déterminer la visibilité de la classe.  
  
 [!code-cpp[Conceptual.Types.ViewInfo#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source2.cpp#2)]
 [!code-csharp[Conceptual.Types.ViewInfo#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source2.cs#2)]
 [!code-vb[Conceptual.Types.ViewInfo#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source2.vb#2)]  
  
 L'exemple suivant recherche le type du membre spécifié.  Il effectue une réflexion sur un membre de la classe **MemberInfo**, puis affiche son type.  
  
 [!code-cpp[Conceptual.Types.ViewInfo#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source3.cpp#3)]
 [!code-csharp[Conceptual.Types.ViewInfo#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source3.cs#3)]
 [!code-vb[Conceptual.Types.ViewInfo#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source3.vb#3)]  
  
 L'exemple suivant utilise toutes les classes Reflection **\*Info** avec <xref:System.Reflection.BindingFlags> pour répertorier tous les membres \(constructeurs, champs, propriétés, événements et méthodes\) de la classe spécifiée et les afficher en deux catégories : statique et instance.  
  
 [!code-cpp[Conceptual.Types.ViewInfo#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source4.cpp#4)]
 [!code-csharp[Conceptual.Types.ViewInfo#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source4.cs#4)]
 [!code-vb[Conceptual.Types.ViewInfo#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source4.vb#4)]  
  
## Voir aussi  
 <xref:System.Reflection.BindingFlags>   
 <xref:System.Reflection.Assembly.GetType%2A?displayProperty=fullName>   
 <xref:System.Reflection.Assembly.GetTypes%2A?displayProperty=fullName>   
 <xref:System.Type.GetType%2A?displayProperty=fullName>   
 <xref:System.Type.GetMembers%2A?displayProperty=fullName>   
 <xref:System.Type.GetFields%2A?displayProperty=fullName>   
 <xref:System.Reflection.Module.GetType%2A?displayProperty=fullName>   
 <xref:System.Reflection.Module.GetTypes%2A?displayProperty=fullName>   
 <xref:System.Reflection.MemberInfo>   
 <xref:System.Reflection.ConstructorInfo>   
 <xref:System.Reflection.MethodInfo>   
 <xref:System.Reflection.FieldInfo>   
 <xref:System.Reflection.EventInfo>   
 <xref:System.Reflection.ParameterInfo>   
 [Réflexion et types génériques](../../../docs/framework/reflection-and-codedom/reflection-and-generic-types.md)