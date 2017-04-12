---
title: /bugreport | Documents Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- -bugreport compiler option [Visual Basic]
- bugreport compiler option [Visual Basic]
- /bugreport compiler option [Visual Basic]
ms.assetid: e4325406-8dbd-4b48-b311-9ee0799e48bb
caps.latest.revision: 22
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 9c64ec49d7e6842edbc0fed7407a34132a8f5a88
ms.lasthandoff: 03/13/2017

---
# <a name="bugreport"></a>/bugreport
Crée un fichier que vous pouvez utiliser lorsque vous archivez un rapport de bogue.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/bugreport:file  
```  
  
## <a name="arguments"></a>Arguments  
  
|Terme|Définition|  
|---|---|  
|`file`|Obligatoire. Le nom du fichier qui contient votre rapport de bogue. Placez le nom de fichier entre guillemets ( » «) si le nom contient un espace.|  
  
## <a name="remarks"></a>Remarques  
 Les informations suivantes sont ajoutées à `file`:  
  
-   Une copie de tous les fichiers de code source dans la compilation.  
  
-   Une liste des options du compilateur utilisé dans la compilation.  
  
-   Informations de version concernant votre compilateur, le common language runtime et le système d’exploitation.  
  
-   Sortie du compilateur, le cas échéant.  
  
-   Description du problème pour lequel vous êtes invité.  
  
-   Une description de la façon dont vous pensez que le problème doit être corrigée, pour lequel vous êtes invité.  
  
 Parce qu’une copie de tous les fichiers de code source est incluse dans `file`, vous pouvez souhaiter reproduire l’erreur de code (supposée) dans le programme le plus court possible.  
  
> [!IMPORTANT]
>  La `/bugreport` option génère un fichier qui contient des informations potentiellement sensibles. Cela inclut l’heure actuelle, la version du compilateur, [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] version, version du système d’exploitation, nom d’utilisateur, les arguments de ligne de commande avec laquelle le compilateur a été exécuté, tout le code source, et la forme binaire de tout assembly référencé. Cette option est accessible en spécifiant des options de ligne de commande dans le fichier Web.config pour une compilation côté serveur d’un [!INCLUDE[vstecasp](../../../csharp/language-reference/preprocessor-directives/includes/vstecasp_md.md)] application. Pour éviter ce problème, modifiez le fichier Machine.config pour ne pas autoriser les utilisateurs à partir de la compilation sur le serveur.  
  
 Si cette option est utilisée avec `/errorreport:prompt`, `/errorreport:queue`, ou `/errorreport:send`, et que votre application rencontre une erreur interne du compilateur, les informations contenues dans `file` sont envoyées à Microsoft Corporation. Ces informations aideront les ingénieurs Microsoft à identifier la cause de l’erreur et peut aider à améliorer la prochaine version de [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]. Par défaut, aucune information n’est envoyée à Microsoft. Toutefois, lorsque vous compilez une application à l’aide de `/errorreport:queue`, qui est activé par défaut, l’application rassemble ses rapports d’erreurs. Ensuite, lorsque l’administrateur de l’ordinateur se connecte, le système de création de rapports d’erreurs affiche une fenêtre indépendante qui autorise l’administrateur à envoyer à Microsoft les rapports d’erreur survenus depuis l’ouverture de session.  
  
> [!NOTE]
>  La `/bugreport` option n’est pas disponible dans l’environnement de développement Visual Studio ; il est disponible uniquement lorsque vous compilez à partir de la ligne de commande.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant compile `T2.vb` et place toutes les informations de rapport de bogue dans le fichier `Problem.txt`.  
  
```  
vbc /bugreport:problem.txt t2.vb  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)   
 [/Debug (Visual Basic)](../../../visual-basic/reference/command-line-compiler/debug.md)   
 [/errorreport](../../../visual-basic/reference/command-line-compiler/errorreport.md)   
 [Exemples de lignes de commande Compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)   
 [trustLevel, élément de securityPolicy (schéma des paramètres ASP.NET)](http://msdn.microsoft.com/en-us/729ab04c-03da-4ee5-86b1-be9d08a09369)
