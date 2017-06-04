---
title: "Comment&#160;: utiliser la protection des donn&#233;es | Microsoft Docs"
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
  - "chiffrement (.NET Framework), API de protection des données"
  - "données (.NET Framework), déchiffrement"
  - "données (.NET Framework), chiffrement"
  - "API de protection des données (.NET Framework)"
  - "déchiffrement"
  - "DPAPI"
  - "chiffrement (.NET Framework), API de protection des données"
  - "ProtectedData (classe), à propos de la classe ProtectedData"
  - "ProtectedMemory (classe), à propos de la classe ProtectedMemory"
ms.assetid: 606698b0-cb1a-42ca-beeb-0bea34205d20
caps.latest.revision: 11
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 11
---
# Comment&#160;: utiliser la protection des donn&#233;es
.NET Framework fournit l'accès à l'API de protection des données \(DPAPI\), qui permet de chiffrer des données à l'aide des informations de compte de l'utilisateur ou de l'ordinateur actuel.  Quand vous utilisez l'API de protection des données, vous simplifiez le processus de génération et de stockage explicites de la clé de chiffrement.  
  
 Utilisez la classe <xref:System.Security.Cryptography.ProtectedMemory> pour chiffrer un tableau d'octets en mémoire.  Cette fonctionnalité est disponible dans Microsoft Windows XP et les systèmes d'exploitation ultérieurs.  Vous pouvez spécifier que la mémoire chiffrée par le processus actuel peut être déchiffrée par le processus actuel uniquement, par tous les processus ou dans le même contexte utilisateur.  Reportez\-vous à l'énumération <xref:System.Security.Cryptography.MemoryProtectionScope> pour obtenir une description détaillée des options <xref:System.Security.Cryptography.ProtectedMemory>.  
  
 Utilisez la classe <xref:System.Security.Cryptography.ProtectedData> pour chiffrer une copie d'un tableau d'octets.  Cette fonctionnalité est disponible dans Microsoft Windows 2000 et les systèmes d'exploitation ultérieurs.  Vous pouvez spécifier que les données chiffrées par le compte d'utilisateur actuel peuvent être déchiffrées uniquement par le même compte d'utilisateur, ou bien par n'importe quel compte de l'ordinateur.  Reportez\-vous à l'énumération <xref:System.Security.Cryptography.DataProtectionScope> pour obtenir une description détaillée des options <xref:System.Security.Cryptography.ProtectedData>.  
  
### Pour chiffrer les données en mémoire à l'aide de la protection des données  
  
1.  Appelez la méthode statique <xref:System.Security.Cryptography.ProtectedMemory.Protect%2A> en passant un tableau d'octets à chiffrer, l'entropie et la portée de protection de mémoire.  
  
### Pour déchiffrer les données en mémoire à l'aide de la protection des données  
  
1.  Appelez la méthode statique <xref:System.Security.Cryptography.ProtectedMemory.Unprotect%2A> en passant un tableau d'octets à déchiffrer et la portée de protection de mémoire.  
  
### Pour chiffrer les données d'un fichier ou d'un flux à l'aide de la protection des données  
  
1.  Créez une entropie aléatoire.  
  
2.  Appelez la méthode statique <xref:System.Security.Cryptography.ProtectedData.Protect%2A> en passant un tableau d'octets à chiffrer, l'entropie et la portée de protection des données.  
  
3.  Écrivez les données chiffrées dans un fichier ou un flux.  
  
### Pour déchiffrer les données à partir d'un fichier ou d'un flux à l'aide de la protection des données  
  
1.  Lisez les données chiffrées à partir d'un fichier ou d'un flux.  
  
2.  Appelez la méthode statique <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A> en passant un tableau d'octets à déchiffrer et la portée de protection des données.  
  
## Exemple  
 L'exemple de code suivant montre deux formes de chiffrement et de déchiffrement.  Tout d'abord, l'exemple de code chiffre et déchiffre un tableau d'octets en mémoire.  Ensuite, l'exemple de code chiffre une copie d'un tableau d'octets, l'enregistre dans un fichier, charge les données à partir du fichier, puis déchiffre les données.  L'exemple affiche les données d'origine, les données chiffrées et les données déchiffrées.  
  
 [!code-csharp[DPAPI-HowTO#1](../../../samples/snippets/csharp/VS_Snippets_CLR/DPAPI-HowTO/cs/sample.cs#1)]
 [!code-vb[DPAPI-HowTO#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DPAPI-HowTO/vb/sample.vb#1)]  
  
## Compilation du code  
  
-   Incluez une référence à `System.Security.dll`.  
  
-   Incluez les espaces de noms <xref:System>, <xref:System.IO>, <xref:System.Security.Cryptography> et <xref:System.Text>.  
  
## Voir aussi  
 <xref:System.Security.Cryptography.ProtectedMemory>   
 <xref:System.Security.Cryptography.ProtectedData>