---
title: /errorreport
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- -errorreport compiler option [Visual Basic]
- /errorreport compiler option [Visual Basic]
- errorreport compiler option [Visual Basic]
ms.assetid: a7fe83a2-a6d8-460c-8dad-79a8f433f501
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0abe276aaacdeb175c3af7067dffa81448450e22
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="errorreport"></a>/errorreport
Indique comment le compilateur [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] doit signaler les erreurs internes du compilateur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/errorreport:{ prompt | queue | send | none }  
```  
  
## <a name="remarks"></a>Remarques  
 Cette option fournit un moyen pratique de rapport un [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] erreur interne du compilateur (ICE) pour le [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] équipe de Microsoft. Par défaut, le compilateur n’envoie aucune information à Microsoft. Toutefois, si vous rencontrez une erreur interne du compilateur, cette option vous permet de signaler l’erreur à Microsoft. Ces informations aideront les ingénieurs de Microsoft à identifier la cause et peut aider à améliorer la prochaine version de [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].  
  
 Capacité d’un utilisateur d’envoyer des rapports dépend des autorisations de stratégie ordinateur et utilisateur.  
  
 Le tableau suivant résume l’effet de la `/errorreport` option.  
  
|Option|Comportement|  
|---|---|  
|`prompt`|Si une erreur interne du compilateur se produit, une boîte de dialogue s’affiche afin que vous puissiez afficher les données collectées par le compilateur. Vous pouvez déterminer s’il existe des informations sensibles dans le rapport d’erreurs et prendre une décision quant à envoyer à Microsoft. Si vous décidez d’envoyer, et les paramètres de stratégie ordinateur et utilisateur pour lui permettent, le compilateur envoie les données à Microsoft.|  
|`queue`|Met le rapport d’erreurs en file d’attente. Lorsque vous vous connectez avec des privilèges d’administrateur, vous pouvez signaler les erreurs depuis la dernière fois que vous étiez connecté (vous ne serez pas invité à envoyer des rapports pour les échecs de plus d’une fois tous les trois jours). Il s’agit du comportement par défaut lors de la `/errorreport` option n’est pas spécifiée.|  
|`send`|Si une erreur interne du compilateur se produit et les paramètres de stratégie ordinateur et utilisateur pour lui permettent, le compilateur envoie les données à Microsoft.<br /><br /> L’option `/errorReport:send` tente d’envoyer automatiquement les informations d’erreur à Microsoft. Cette option dépend du Registre. Pour plus d’informations sur les valeurs appropriées dans le Registre, consultez [comment activer le rapport d’erreurs automatique dans les outils de ligne de commande de Visual Studio 2008](http://go.microsoft.com/fwlink/?LinkID=184695).|  
|`none`|Si une erreur interne du compilateur se produit, il ne sera pas collectée ou envoyée à Microsoft.|  
  
 Le compilateur envoie les données qui comprend la pile au moment de l’erreur, qui inclut généralement du code source. Si `/errorreport` est utilisé avec le [/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md) option, l’intégralité du fichier source est envoyé.  
  
 Il est préférable d’utiliser cette option avec la [/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md) option, car elle permet aux ingénieurs Microsoft plus facilement de reproduire l’erreur.  
  
> [!NOTE]
>  Le `/errorreport` option n’est pas disponible dans l’environnement de développement Visual Studio ; il est disponible uniquement lors de la compilation à partir de la ligne de commande.  
  
## <a name="example"></a>Exemple  
 Le code suivant tente de compiler `T2.vb`, et si le compilateur rencontre une erreur interne du compilateur, il vous invite à envoyer le rapport d’erreurs à Microsoft.  
  
```  
vbc /errorreport:prompt t2.vb  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)
