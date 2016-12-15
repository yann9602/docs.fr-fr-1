---
title: "/delaysign (C# Compiler Options) | Microsoft Docs"
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
  - "/delaysign"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "-delaysign compiler option [C#]"
  - "delaysign compiler option [C#]"
  - "/delaysign compiler option [C#]"
ms.assetid: bcb058eb-2933-4e7f-b356-5c941db4de75
caps.latest.revision: 16
caps.handback.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /delaysign (C# Compiler Options)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Cette option oblige le compilateur à réserver un espace dans le fichier de sortie afin qu'une signature numérique puisse être ajoutée ultérieurement.  
  
## Syntaxe  
  
```  
/delaysign[ + | - ]  
```  
  
## Arguments  
 `+` &#124; `-`  
 Utilisez **\/delaysign\-** si vous souhaitez obtenir un assembly complètement signé.  Utilisez **\/delaysign\+** si vous souhaitez uniquement placer la clé publique dans l'assembly.  La valeur par défaut est **\/delaysign\-**.  
  
## Notes  
 L'option **\/delaysign** ne produit aucun effet, sauf lorsqu'elle est utilisée avec [\/keyfile](../../../csharp/language-reference/compiler-options/keyfile-compiler-option.md) ou [\/keycontainer](../../../csharp/language-reference/compiler-options/keycontainer-compiler-option.md).  
  
 Lorsque vous demandez un assembly complètement signé, le compilateur hache le fichier contenant le manifeste \(métadonnées de l'assembly\) et signe ce hachage avec la clé privée.  La signature numérique obtenue est stockée dans le fichier qui contient le manifeste.  Lorsque la signature d'un assembly est différée, le compilateur ne calcule ni ne stocke la signature, mais réserve un espace dans le fichier pour pouvoir y ajouter ultérieurement la signature.  
  
 Par exemple, l'utilisation de **\/delaysign\+** permet à un testeur d'insérer l'assembly dans le cache global.  Après le test, vous pouvez signer complètement l'assembly en y plaçant la clé privée à l'aide de l'utilitaire [Assembly Linker](../Topic/Al.exe%20\(Assembly%20Linker\).md).  
  
 Pour plus d'informations, consultez [Création et utilisation d'assemblys avec nom fort](../Topic/Creating%20and%20Using%20Strong-Named%20Assemblies.md) et [Temporisation de signature d'un assembly](../Topic/Delay%20Signing%20an%20Assembly.md).  
  
### Pour définir cette option du compilateur dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la page **Propriétés** du projet.  
  
2.  Modifiez la propriété **Temporiser la signature uniquement**.  
  
 Pour plus d'informations sur la définition de cette option du compilateur par programme, consultez <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>.  
  
## Voir aussi  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [Comment : modifier des propriétés de projet et des paramètres de configuration](http://msdn.microsoft.com/fr-fr/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)