---
title: "/codepage (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "/codepage compiler option [Visual Basic]"
  - "codepage compiler option [Visual Basic]"
  - "-codepage compiler option [Visual Basic]"
ms.assetid: be36ec33-6800-4505-838c-4124564f5cc9
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 17
---
# /codepage (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Spécifie la page de codes à utiliser pour tous les fichiers de code source inclus dans la compilation.  
  
## Syntaxe  
  
```  
/codepage:id  
```  
  
## Arguments  
  
|||  
|-|-|  
|Terme|Définition|  
|`id`|Requis.  Le compilateur utilise la page de codes spécifiée par `id` pour interpréter l'encodage des fichiers sources.|  
  
## Notes  
 Pour compiler le code source enregistré avec un encodage spécifique, vous pouvez utiliser `/codepage` pour spécifier quelle page de codes doit être utilisée.  L'option `/codepage` s'applique à tous les fichiers de code source inclus dans votre compilation.  Pour plus d’informations, consultez [Encodage de caractères dans le .NET Framework](../Topic/Character%20Encoding%20in%20the%20.NET%20Framework.md).  
  
 L'option `/codepage` n'est pas nécessaire si les fichiers de code de source ont été enregistrés à l'aide de la page de codes ANSI actuelle, Unicode ou UTF\-8 avec une signature.  [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs-md.md)] enregistre par défaut tous les fichiers de source de code avec la page de codes ANSI actuelle, à moins que l'utilisateur spécifie un autre encodage dans la boîte de dialogue **Encodage**.  [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs-md.md)] utilise la boîte de dialogue **Encodage** pour ouvrir des fichiers de source de code enregistrés avec une page de codes différente.  
  
> [!NOTE]
>  L'option `/codepage` n'est pas accessible dans l'environnement de développement [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs-md.md)]. Elle est disponible uniquement lors de la compilation à partir de la ligne de commande.  
  
## Voir aussi  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)