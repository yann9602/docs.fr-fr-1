---
title: "Comment&#160;: utiliser des caract&#232;res sp&#233;ciaux en XAML | Microsoft Docs"
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
  - "caractères, spécial"
  - "caractères spéciaux"
  - "typographie, caractères spéciaux"
  - "Unicode UTF-8 (format de fichier)"
  - "UTF-8 (format de fichier)"
ms.assetid: a57776d1-f353-4794-afa0-bfa3c712ed1c
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 3
---
# Comment&#160;: utiliser des caract&#232;res sp&#233;ciaux en XAML
Les fichiers balise créés dans [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] sont automatiquement enregistrés dans le format de fichier [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] UTF\-8, ce qui signifie que la plupart des caractères spéciaux \(accents, par exemple\) sont encodés correctement.  Il existe toutefois un jeu de caractères spéciaux utilisés fréquemment qui sont gérés différemment.  Ces caractères spéciaux suivent la norme d'encodage [!INCLUDE[TLA#tla_w3c](../../../../includes/tlasharptla-w3c-md.md)][!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)].  
  
 Le tableau suivant présente la syntaxe utilisée pour encoder ce jeu de caractères spéciaux :  
  
|Caractère|Syntaxe|Description|  
|---------------|-------------|-----------------|  
|\<|`<`|Symbole inférieur à.|  
|\>|`>`|Signe supérieur à.|  
|&|`&`|Symbole de perluète.|  
|"|`"`|Symbole de guillemet double.|  
  
> [!NOTE]
>  Si vous créez un fichier balise à l'aide d'un éditeur de texte, tel que le Bloc\-notes [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)], vous devez enregistrer le fichier au format [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] UTF\-8 pour conserver tous caractères spéciaux encodés.  
  
 L'exemple suivant montre comment utiliser des caractères spéciaux dans le texte lors de la création de la balise.  
  
## Exemple  
 [!code-xml[SpecialCharsSnippets#SpecialCharsSnippet1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpecialCharsSnippets/CS/Window1.xaml#specialcharssnippet1)]