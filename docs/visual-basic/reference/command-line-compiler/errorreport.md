---
title: "/errorreport | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "-errorreport compiler option [Visual Basic]"
  - "/errorreport compiler option [Visual Basic]"
  - "errorreport compiler option [Visual Basic]"
ms.assetid: a7fe83a2-a6d8-460c-8dad-79a8f433f501
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# /errorreport
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Spécifie comment le compilateur [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] doit rapporter les erreurs internes du compilateur.  
  
## Syntaxe  
  
```  
/errorreport:{ prompt | queue | send | none }  
```  
  
## Notes  
 Cette option offre un moyen pratique de signaler une erreur interne du compilateur [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] à l'équipe [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] de Microsoft.  Par défaut, le compilateur n'envoie aucune information à Microsoft.  Toutefois, si vous rencontrez une erreur interne du compilateur, cette option vous permet de la signaler à Microsoft.  Ces informations aideront les ingénieurs Microsoft à identifier la cause et contribueront peut\-être à améliorer la prochaine version de [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  
  
 La capacité d'un utilisateur à envoyer des rapports dépend de l'ordinateur et des autorisations de la stratégie de l'utilisateur.  
  
 Le tableau suivant résume l'effet de l'option `/errorreport`.  
  
|||  
|-|-|  
|Option|Comportement|  
|`prompt`|Si une erreur interne du compilateur se produit, une boîte de dialogue apparaît afin que vous puissiez consulter les données exactes collectées par le compilateur.  Vous pouvez déterminer si des informations sensibles sont contenues dans le rapport d'erreurs et prendre une décision quant à son envoi à Microsoft.  Si vous décidez d'envoyer le rapport et si les paramètres de stratégie de l'ordinateur et de l'utilisateur l'autorisent, le compilateur envoie les données à Microsoft.|  
|`queue`|Met en file d'attente le rapport d'erreurs.  Lorsque vous vous connectez avec des droits d'administrateur, vous pouvez créer un rapport des défaillances survenues depuis votre dernière connexion \(vous ne serez pas invité plus d'une fois tous les trois jours à envoyer des rapports pour les défaillances\).  C'est le comportement par défaut lorsque l'option `/errorreport` n'est pas spécifiée.|  
|`send`|Si une erreur interne du compilateur se produit et si les paramètres de stratégie de l'ordinateur et de l'utilisateur l'autorisent, le compilateur envoie les données à Microsoft.<br /><br /> L'option `/errorReport:send` tente d'envoyer automatiquement des informations d'erreur à Microsoft.  Cette option dépend du Registre.  Pour plus d'informations sur la définition des valeurs appropriées dans le Registre, consultez [How to Turn on Automatic Error Reporting in Visual Studio 2008 Command\-line Tools](http://go.microsoft.com/fwlink/?LinkID=184695).|  
|`none`|Si une erreur interne du compilateur se produit, elle n'est pas collectée ou envoyée à Microsoft.|  
  
 Les données envoyées par le compilateur contiennent la pile au moment de l'erreur, qui renferme d'habitude du code source.  Si `/errorreport` est utilisé avec l'option [\/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md), le fichier source entier est transmis.  
  
 Il est préférable d'utiliser cette option avec l'option [\/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md), car elle permet aux ingénieurs Microsoft de reproduire l'erreur plus facilement.  
  
> [!NOTE]
>  L'option `/errorreport` n'est pas disponible dans l'environnement de développement Visual Studio. Elle est disponible uniquement lors de la compilation à partir de la ligne de commande.  
  
## Exemple  
 Le code suivant essaie de compiler `T2.vb`, et si le compilateur rencontre une erreur interne du compilateur, il vous invite à envoyer le rapport d'erreurs à Microsoft.  
  
```  
vbc /errorreport:prompt t2.vb  
```  
  
## Voir aussi  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)   
 [\/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)