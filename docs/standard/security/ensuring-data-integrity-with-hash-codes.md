---
title: "Garantie de l&#39;int&#233;grit&#233; des donn&#233;es &#224; l&#39;aide des codes de hachage | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "contrôler les codes de hachage"
  - "chiffrement (.NET Framework), hachage"
  - "intégrité des données"
  - "chiffrement (.NET Framework), hachage"
  - "générer le hachage"
  - "hachage"
  - "vérifier les codes de hachage"
ms.assetid: 33660f33-b70f-4dca-8c87-ab35cfc2961a
caps.latest.revision: 14
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 14
---
# Garantie de l&#39;int&#233;grit&#233; des donn&#233;es &#224; l&#39;aide des codes de hachage
Une valeur de hachage est une valeur numérique de longueur fixe qui identifie les données de manière unique.  Les valeurs de hachage permettent de représenter les grandes quantités de données sous forme de valeurs numériques beaucoup plus petites pour qu'elles puissent être utilisées avec des signatures numériques.  Il est plus efficace de signer une valeur de hachage que de signer une valeur élevée.  De même, les valeurs de hachage s'avèrent utiles pour vérifier l'intégrité des données envoyées via des canaux non sécurisés.  La valeur de hachage des données reçues peut être comparée à celle des données envoyées pour déterminer si les données ont été modifiées.  
  
 Cette rubrique explique comment générer et vérifier des codes de hachage en utilisant les classes de l'espace de noms <xref:System.Security.Cryptography?displayProperty=fullName>.  
  
## Génération d'un hachage  
 Les classes de hachage managées peuvent hacher un tableau d'octets ou un objet de flux managé.  Dans l'exemple suivant, l'algorithme de hachage SHA1 est utilisé pour créer une valeur de hachage pour une chaîne.  L'exemple utilise la classe <xref:System.Text.UnicodeEncoding> pour convertir la chaîne en tableau d'octets qui sont hachés à l'aide de la classe <xref:System.Security.Cryptography.SHA1Managed>.  La valeur de hachage est ensuite affichée dans la console.  
  
 [!code-csharp[GeneratingAHash#1](../../../samples/snippets/csharp/VS_Snippets_CLR/generatingahash/cs/program.cs#1)]
 [!code-vb[GeneratingAHash#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/generatingahash/vb/program.vb#1)]  
  
 Ce code affiche la chaîne suivante dans la console :  
  
 `59 4 248 102 77 97 142 201 210 12 224 93 25 41 100 197 213 134 130 135`  
  
## Vérification d'un hachage  
 Les données peuvent être comparées à une valeur de hachage pour déterminer leur intégrité.  En règle générale, les données sont hachées à un certain moment et la valeur de hachage est protégée d'une certaine façon.  Par la suite, les données peuvent être hachées à nouveau et comparées à la valeur protégée.  Si les valeurs de hachage correspondent, cela signifie que les données n'ont pas été modifiées.  Si les valeurs ne correspondent pas, les données ont été endommagées.  Pour que ce système fonctionne, le hachage protégé doit être chiffré ou tenu secret de toutes les tiers non approuvés.  
  
 Dans l'exemple suivant, la valeur de hachage précédente d'une chaîne est comparée à une nouvelle valeur de hachage.  Dans cet exemple, chaque octet des valeurs de hachage est parcouru en boucle et une comparaison est effectuée.  
  
 [!code-csharp[VerifyingAHash#1](../../../samples/snippets/csharp/VS_Snippets_CLR/verifyingahash/cs/program.cs#1)]
 [!code-vb[VerifyingAHash#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/verifyingahash/vb/program.vb#1)]  
  
 Si les deux valeurs de hachage correspondent, voici ce que ce code affiche dans la console :  
  
```  
The hash codes match.  
```  
  
 Si elles ne correspondent pas, le code affiche ce qui suit :  
  
```  
The hash codes do not match.  
```  
  
## Voir aussi  
 [Services de chiffrement](../../../docs/standard/security/cryptographic-services.md)