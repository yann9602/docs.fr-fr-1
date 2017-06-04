---
title: "Remplissage de cha&#238;nes dans .NET Framework | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "remplir des chaînes"
  - "PadLeft (méthode)"
  - "PadRight (méthode)"
  - "chaînes (.NET Framework), marge intérieure"
  - "espace blanc"
ms.assetid: 84a9f142-3244-4c90-ba02-21af9bbaff71
caps.latest.revision: 12
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 12
---
# Remplissage de cha&#238;nes dans .NET Framework
Utilisez l'une des méthodes <xref:System.String> suivantes pour créer une nouvelle chaîne se composant d'une chaîne d'origine remplie à l'aide de caractères de début ou de fin sur une longueur totale spécifiée.  Le caractère de remplissage peut être un espace ou un caractère spécifié ; il apparaît donc aligné à droite ou aligné à gauche.  
  
|Nom de la méthode|Utilisation|  
|-----------------------|-----------------|  
|<xref:System.String.PadLeft%2A?displayProperty=fullName>|Remplit une chaîne à l'aide de caractères de début sur une longueur totale spécifiée.|  
|<xref:System.String.PadRight%2A?displayProperty=fullName>|Remplit une chaîne à l'aide de caractères de fin sur une longueur totale spécifiée.|  
  
## PadLeft  
 La méthode <xref:System.String.PadLeft%2A?displayProperty=fullName> crée une nouvelle chaîne en concaténant suffisamment de caractères de remplissage de début à une chaîne d'origine pour atteindre une longueur totale spécifiée.  La méthode <xref:System.String.PadLeft%28System.Int32%29?displayProperty=fullName> utilise l'espace blanc comme caractère de remplissage et la méthode <xref:System.String.PadLeft%28System.Int32%2CSystem.Char%29?displayProperty=fullName> vous permet de spécifier votre propre caractère de remplissage.  
  
 L'exemple de code suivant utilise la méthode <xref:System.String.PadLeft%2A> pour créer une nouvelle chaîne longue de vingt caractères.  L'exemple affiche « `--------Hello World!` » sur la console.  
  
 [!code-cpp[Conceptual.String.BasicOps#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#3)]
 [!code-csharp[Conceptual.String.BasicOps#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#3)]
 [!code-vb[Conceptual.String.BasicOps#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#3)]  
  
## PadRight  
 La méthode <xref:System.String.PadRight%2A?displayProperty=fullName> crée une nouvelle chaîne en concaténant suffisamment de caractères de remplissage de fin à une chaîne d'origine pour atteindre une longueur totale spécifiée.  La méthode <xref:System.String.PadRight%28System.Int32%29?displayProperty=fullName> utilise l'espace blanc comme caractère de remplissage et la méthode <xref:System.String.PadRight%28System.Int32%2CSystem.Char%29?displayProperty=fullName> vous permet de spécifier votre propre caractère de remplissage.  
  
 L'exemple de code suivant utilise la méthode <xref:System.String.PadRight%2A> pour créer une nouvelle chaîne longue de vingt caractères.  L'exemple affiche « `Hello World!--------` » sur la console.  
  
 [!code-cpp[Conceptual.String.BasicOps#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#4)]
 [!code-csharp[Conceptual.String.BasicOps#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#4)]
 [!code-vb[Conceptual.String.BasicOps#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#4)]  
  
## Voir aussi  
 [Opérations de chaînes de base](../../../docs/standard/base-types/basic-string-operations.md)