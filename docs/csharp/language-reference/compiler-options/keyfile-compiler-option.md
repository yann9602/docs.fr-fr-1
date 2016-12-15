---
title: "/keyfile (C# Compiler Options) | Microsoft Docs"
ms.custom: ""
ms.date: "12/13/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/keyfile"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "/keyfile compiler option [C#]"
  - "-keyfile compiler option [C#]"
  - "keyfile compiler option [C#]"
ms.assetid: 0815f9de-ace4-4e98-b4c6-13c55dea40c2
caps.latest.revision: 15
caps.handback.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /keyfile (C# Compiler Options)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Spécifie le nom de fichier contenant la clé de chiffrement.  
  
## Syntaxe  
  
```  
/keyfile:file  
```  
  
## Arguments  
  
|Terme|Définition|  
|-----------|----------------|  
|`file`|Nom du fichier contenant la clé de nom fort.|  
  
## Notes  
 Lorsque cette option est utilisée, le compilateur insère la clé publique du fichier spécifié dans le manifeste d'assembly, puis signe le dernier assembly avec la clé privée.  Pour générer un fichier de clé, tapez sn \-k `file` sur la ligne de commande.  
  
 Si vous compilez à l'aide de **\/target:module**, le nom du fichier de clés est conservé dans le module et incorporé dans l'assembly qui est créé lorsque vous compilez une application à l'aide de [\/addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md).  
  
 Vous pouvez également passer vos informations de chiffrement au compilateur avec [\/keycontainer](../../../csharp/language-reference/compiler-options/keycontainer-compiler-option.md).  Utilisez [\/delaysign](../../../csharp/language-reference/compiler-options/delaysign-compiler-option.md) si vous souhaitez obtenir un assembly partiellement signé.  
  
 Si \/keyfile et \/keycontainer sont tous deux spécifiés \(par une option de ligne de commande ou par un attribut personnalisé\) dans la même compilation, le compilateur tente d'abord le conteneur de clé.  Si cette tentative aboutit, l'assembly est signé avec les informations figurant dans le conteneur de clé.  Si le compilateur ne trouve pas le conteneur de clé, il tente le fichier spécifié avec \/keyfile.  Si cette tentative aboutit, l'assembly est signé avec les informations du fichier de clé et les informations de clé sont installées dans le conteneur de clé \(résultat similaire à celui de sn \-i\) afin que, lors de la prochaine compilation, le conteneur de clé soit valide.  
  
 Notez qu'un fichier de clé pourrait contenir uniquement la clé publique.  
  
 Pour plus d'informations, consultez [Création et utilisation d'assemblys avec nom fort](../Topic/Creating%20and%20Using%20Strong-Named%20Assemblies.md) et [Temporisation de signature d'un assembly](../Topic/Delay%20Signing%20an%20Assembly.md).  
  
### Pour définir cette option du compilateur dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la page **Propriétés** du projet.  
  
2.  Cliquez sur la page de propriétés **Signature**.  
  
3.  Modifiez la propriété **Choisir un fichier de clé de nom fort**.  
  
 Vous pouvez accéder par programme à cette option du compilateur avec <xref:VSLangProj.ProjectProperties.AssemblyOriginatorKeyFile%2A>.  
  
## Voir aussi  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [Comment : modifier des propriétés de projet et des paramètres de configuration](http://msdn.microsoft.com/fr-fr/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)