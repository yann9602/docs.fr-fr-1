---
title: "Comment&#160;: acc&#233;der aux p&#233;riph&#233;riques de chiffrement du mat&#233;riel | Microsoft Docs"
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
  - "chiffrement"
  - "CspParameters"
  - "chiffrement"
  - "chiffrement du matériel"
  - "carte de clé"
ms.assetid: b0e734df-6eb4-4b16-b48c-6f0fe82d5f17
caps.latest.revision: 9
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 9
---
# Comment&#160;: acc&#233;der aux p&#233;riph&#233;riques de chiffrement du mat&#233;riel
Vous pouvez utiliser la classe <xref:System.Security.Cryptography.CspParameters> pour accéder aux périphériques de chiffrement matériel.  Par exemple, vous pouvez utiliser cette classe pour intégrer votre application à une carte à puce, à un générateur matériel de nombres aléatoires ou à une implémentation matérielle d'un algorithme de chiffrement.  
  
 La classe <xref:System.Security.Cryptography.CspParameters> crée un fournisseur de services de chiffrement \(CSP\) qui accède à un périphérique de chiffrement matériel correctement installé.  Vous pouvez vérifier la disponibilité d'un fournisseur de services de chiffrement en inspectant la clé de Registre suivante à l'aide de l'Éditeur du Registre \(Regedit.exe\) : HKEY\_LOCAL\_MACHINE\\Software\\Microsoft\\Cryptography\\Defaults\\Provider.  
  
### Pour signer des données à l'aide d'une carte de clé  
  
1.  Créez une instance de la classe <xref:System.Security.Cryptography.CspParameters>, en passant le type de fournisseur entier et le nom du fournisseur au constructeur.  
  
2.  Passez les indicateurs appropriés à la propriété <xref:System.Security.Cryptography.CspParameters.Flags%2A> du nouvel objet <xref:System.Security.Cryptography.CspParameters>.  Par exemple, passez l'indicateur <xref:System.Security.Cryptography.CspProviderFlags>.  
  
3.  Créez une instance d'une classe <xref:System.Security.Cryptography.AsymmetricAlgorithm> \(par exemple, la classe <xref:System.Security.Cryptography.RSACryptoServiceProvider>\), en passant l'objet <xref:System.Security.Cryptography.CspParameters> au constructeur.  
  
4.  Signez vos données à l'aide de l'une des méthodes `Sign`, puis vérifiez vos données à l'aide de l'une des méthodes `Verify`.  
  
### Pour générer un nombre aléatoire à l'aide d'un générateur matériel de nombres aléatoires  
  
1.  Créez une instance de la classe <xref:System.Security.Cryptography.CspParameters>, en passant le type de fournisseur entier et le nom du fournisseur au constructeur.  
  
2.  Créez une instance de <xref:System.Security.Cryptography.RNGCryptoServiceProvider>, en passant l'objet <xref:System.Security.Cryptography.CspParameters> au constructeur.  
  
3.  Créez une valeur aléatoire à l'aide de la méthode <xref:System.Security.Cryptography.RNGCryptoServiceProvider.GetBytes%2A> ou <xref:System.Security.Cryptography.RNGCryptoServiceProvider.GetNonZeroBytes%2A>.  
  
## Exemple  
 L'exemple de code suivant montre comment signer des données à l'aide d'une carte à puce.  L'exemple de code crée un objet <xref:System.Security.Cryptography.CspParameters> qui expose une carte à puce, puis initialise un objet <xref:System.Security.Cryptography.RSACryptoServiceProvider> à l'aide du fournisseur de services de chiffrement.  L'exemple de code signe et vérifie certaines données.  
  
 [!code-cpp[Cryptography.SmartCardCSP#1](../../../samples/snippets/cpp/VS_Snippets_CLR/Cryptography.SmartCardCSP/CPP/Cryptography.SmartCardCSP.cpp#1)]
 [!code-csharp[Cryptography.SmartCardCSP#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Cryptography.SmartCardCSP/CS/example.cs#1)]
 [!code-vb[Cryptography.SmartCardCSP#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Cryptography.SmartCardCSP/VB/example.vb#1)]  
  
## Compilation du code  
  
-   Incluez les espaces de noms <xref:System> et <xref:System.Security.Cryptography>.  
  
-   Vous devez disposer d'un lecteur de carte à puce et de pilotes installés sur votre ordinateur.  
  
-   Vous devez initialiser l'objet <xref:System.Security.Cryptography.CspParameters> à l'aide des informations spécifiques à votre lecteur de cartes.  Pour plus d'informations, consultez la documentation de votre lecteur de cartes.