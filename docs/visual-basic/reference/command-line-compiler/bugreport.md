---
title: "/bugreport | Microsoft Docs"
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
  - "-bugreport compiler option [Visual Basic]"
  - "bugreport compiler option [Visual Basic]"
  - "/bugreport compiler option [Visual Basic]"
ms.assetid: e4325406-8dbd-4b48-b311-9ee0799e48bb
caps.latest.revision: 22
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 22
---
# /bugreport
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Crée un fichier qui peut être utilisé lors du classement d'un rapport de bogue.  
  
## Syntaxe  
  
```  
/bugreport:file  
```  
  
## Arguments  
  
|||  
|-|-|  
|Terme|Définition|  
|`file`|Obligatoire.  Nom du fichier dans lequel vous souhaitez inclure votre rapport de bogue.  Mettez le nom de fichier entre guillemets \(""\) s'il contient un espace.|  
  
## Notes  
 Les informations suivantes sont ajoutées à `file` :  
  
-   une copie de tous les fichiers de code source dans la compilation ;  
  
-   une liste des options du compilateur utilisée lors de la compilation ;  
  
-   des informations sur la version du compilateur, du Common Language Runtime et du système d'exploitation ;  
  
-   les résultats de la compilation, le cas échéant ;  
  
-   un message vous invitant à décrire le problème ;  
  
-   un message vous invitant à décrire la façon dont le problème pourrait être résolu, selon vous.  
  
 Comme `file` contient une copie de tous les fichiers de code source, vous pouvez reproduire l'erreur \(supposée\) dans le code avec le programme le plus court possible.  
  
> [!IMPORTANT]
>  L'option `/bugreport` produit un fichier qui contient des informations potentiellement sensibles.  Cela inclut le temps réel, la version du compilateur, la version de [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)], la version du système d'exploitation, le nom d'utilisateur, les arguments de ligne de commande avec lesquels le compilateur a été exécuté, tout le code source ainsi que la forme binaire de tout assembly référencé.  Cette option est accessible en spécifiant des options de ligne de commande dans le fichier Web.config pour une compilation côté serveur d'une application [!INCLUDE[vstecasp](../../../csharp/language-reference/preprocessor-directives/includes/vstecasp-md.md)].  Pour empêcher cela, modifiez le fichier Machine.config afin d'interdire aux utilisateurs de faire une compilation sur le serveur.  
  
 Si cette option est utilisée avec `/errorreport:prompt`, `/errorreport:queue` ou `/errorreport:send` et si votre application rencontre une erreur interne du compilateur, les informations dans `file` sont envoyées à Microsoft Corporation.  Ces informations aideront les ingénieurs Microsoft à identifier la cause de l'erreur et pourront peut\-être permettre d'améliorer la version finale suivante de [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)].  Par défaut, aucune information n'est envoyée à Microsoft.  Toutefois, lorsque vous compilez une application en utilisant `/errorreport:queue` activé par défaut, l'application rassemble ses rapports d'erreurs.  Ensuite, lorsque l'administrateur de l'ordinateur se connecte, le système de rapport d'erreurs affiche une fenêtre indépendante qui autorise l'administrateur à envoyer à Microsoft tous les rapports d'erreurs créés depuis la connexion.  
  
> [!NOTE]
>  L'option `/bugreport` n'est pas disponible dans l'environnement de développement Visual Studio. Elle est disponible uniquement lors de la compilation à partir de la ligne de commande.  
  
## Exemple  
 L'exemple suivant compile `T2.vb` et place toutes les informations de rapport de bogue dans le fichier `Problem.txt`.  
  
```  
vbc /bugreport:problem.txt t2.vb  
```  
  
## Voir aussi  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [\/debug](../../../visual-basic/reference/command-line-compiler/debug.md)   
 [\/errorreport](../../../visual-basic/reference/command-line-compiler/errorreport.md)   
 [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)   
 [trustLevel, élément de securityPolicy \(Schéma des paramètres ASP.NET\)](http://msdn.microsoft.com/fr-fr/729ab04c-03da-4ee5-86b1-be9d08a09369)