---
title: "/delaysign | Microsoft Docs"
ms.custom: ""
ms.date: "12/13/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "delaysign compiler option [Visual Basic]"
  - "/delaysign compiler option [Visual Basic]"
  - "-delaysign compiler option [Visual Basic]"
ms.assetid: c76e61a4-1884-4252-9fb2-377f99caa690
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# /delaysign
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Spécifie si l'assembly sera complètement ou partiellement signé.  
  
## Syntaxe  
  
```  
/delaysign[+ | -]  
```  
  
## Arguments  
 `+` &#124; `-`  
 Facultatif.  Utilisez `/delaysign-` si vous souhaitez obtenir un assembly complètement signé.  Utilisez `/delaysign+` si vous souhaitez placer la clé publique dans l'assembly et réservez de l'espace pour le hachage signé.  La valeur par défaut est `/delaysign-`.  
  
## Notes  
 L'option `/delaysign` est sans effet sauf si elle est utilisée avec [\/keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md) ou [\/keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md).  
  
 Lorsque vous demandez un assembly complètement signé, le compilateur hache le fichier contenant le manifeste \(métadonnées de l'assembly\) et signe ce hachage avec la clé privée.  La signature numérique obtenue est stockée dans le fichier qui contient le manifeste.  Lorsque la signature d'un assembly est différée, le compilateur ne calcule ni ne stocke la signature, mais réserve un espace dans le fichier pour pouvoir y ajouter ultérieurement la signature.  
  
 Par exemple, à l'aide de `/delaysign+`, le développeur d'une organisation peut distribuer des versions de test d'un assembly non signées que les testeurs peuvent enregistrer dans le Global Assembly Cache et utiliser.  Lorsqu'elle a fini de travailler sur l'assembly, la personne responsable de la clé privée de l'organisation peut le signer complètement.  Ce compartimentage protège la clé privée de l'organisation contre la divulgation tout en permettant à tous les développeurs de travailler sur les assemblys.  
  
 Pour plus d'informations sur la signature d'un assembly, consultez [Création et utilisation d'assemblys avec nom fort](../Topic/Creating%20and%20Using%20Strong-Named%20Assemblies.md).  
  
### Pour définir \/temporiser la signature dans l'environnement de développement intégré Visual Studio  
  
1.  Sélectionnez un projet dans l'**Explorateur de solutions**.  Dans le menu **Projet**, cliquez sur **Propriétés**.  Pour plus d'informations, consultez [Introduction to the Project Designer](http://msdn.microsoft.com/fr-fr/898dd854-c98d-430c-ba1b-a913ce3c73d7).  
  
2.  Cliquez sur l'onglet **Signature**.  
  
3.  Définissez la valeur dans la zone **Temporiser la signature uniquement**.  
  
## Voir aussi  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [\/keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md)   
 [\/keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md)   
 [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)