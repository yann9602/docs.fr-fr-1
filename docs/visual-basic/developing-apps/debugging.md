---
title: "Debugging Your Visual Basic Application | Microsoft Docs"
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
  - "debugging [Visual Basic], common tasks"
ms.assetid: 904760b8-9fe9-42a7-9d65-d93774253219
caps.latest.revision: 28
caps.handback.revision: 28
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Debugging Your Visual Basic Application
[!INCLUDE[vs2017banner](../../csharp/includes/vs2017banner.md)]

Cette page fournit des liens vers la documentation relative aux fonctions de débogage intégrées dans [!INCLUDE[vsprvs](../../csharp/includes/vsprvs_md.md)].  Par exemple, vous pouvez rechercher des erreurs sémantiques dans votre application en observant son comportement à l'exécution dans le débogueur lui\-même.  
  
 En utilisant le débogueur, vous pouvez examiner le contenu des variables de votre application sans insérer des appels supplémentaires pour sortir les valeurs.  De même, vous pouvez insérer un point d'arrêt dans votre code pour arrêter l'exécution au point que vous spécifiez.  
  
## Contrôle de l'exécution  
 Le tableau suivant répertorie les tâches de débogage impliquant le contrôle de l'exécution et fournit des liens vers les pages d'aide associées.  
  
|||  
|-|-|  
|Pour|Consultez|  
|Commencez à déboguer un projet Visual Studio, attachez un processus, arrêtez\-vous dans le code, parcourez le code, effectuez une exécution jusqu'au curseur, effectuez une exécution jusqu'à une fonction de la pile des appels, définissez l'instruction suivante, parcourez Uniquement mon code, arrêtez le débogage, redémarrez le débogage ou détachez un processus débogué.|[Naviguer dans le code avec le débogueur](/visual-studio/debugger/navigating-through-code-with-the-debugger)|  
|Spécifiez les configurations pour les versions Release et Debug d'un programme.|[Debug and Release Project Configurations](http://msdn.microsoft.com/fr-fr/0440b300-0614-4511-901a-105b771b236e)|  
|Définir des options de démarrage \(arguments de ligne de commande, répertoire de travail, ordinateur distant\)|[NIB: How to: Set Start Options for Application Debugging](http://msdn.microsoft.com/fr-fr/ce792058-7bac-4dd6-858b-466e872687b8)|  
|Effectuer le débogage au moment du design.|[Procédure pas à pas : débogage au moment du design](../Topic/Walkthrough:%20Debugging%20at%20Design%20Time.md)|  
|Permettre le débogage juste\-à\-temps, qui lance le débogueur Visual Studio lorsqu'un programme qui s'exécute en dehors de Visual Studio rencontre une erreur irrécupérable.|[Débogage juste\-à\-temps](/visual-studio/debugger/just-in-time-debugging-in-visual-studio)|  
|Définissez des points d'arrêt pour les lignes sources, les instructions d'assembly et la fonction de la pile des appels.  Spécifiez les conditions, les nombres d'accès et l'emplacement d'exécution.|[Utilisation des points d'arrêt](/visual-studio/debugger/using-breakpoints)|  
  
## Gestion des exceptions  
 Le tableau suivant répertorie les tâches de débogage relatives à la gestion des exceptions et pointe vers leurs pages d'aide associées.  
  
|||  
|-|-|  
|Pour|Consultez|  
|S'arrêter sur les exceptions non gérées.|[Comment : s'arrêter sur les exceptions non gérées par l'utilisateur](../Topic/How%20to:%20Break%20on%20User-Unhandled%20Exceptions.md)|  
|S'arrêter lorsqu'une exception est levée.|[Comment : arrêter l'exécution lorsqu'une exception est levée](../Topic/How%20to:%20Break%20When%20an%20Exception%20is%20Thrown.md)|  
|S'arrêter sur les exceptions de première\-chance.|[Comment : arrêter l'exécution lorsqu'une exception est levée](../Topic/How%20to:%20Break%20When%20an%20Exception%20is%20Thrown.md)|  
|Utiliser l'Assistant Exception.|[How to: Correct Run\-Time Errors with the Exception Assistant](../Topic/How%20to:%20Correct%20Run-Time%20Errors%20with%20the%20Exception%20Assistant.md)|  
|Ajouter une nouvelle exception.|[Comment : ajouter de nouvelles exceptions](../Topic/How%20to:%20Add%20New%20Exceptions.md)|  
|Poursuivre l'exécution après qu'une exception a été levée.|[Poursuite de l'exécution à la suite d'une exception](/visual-studio/debugger/continuing-execution-after-an-exception)|  
  
## Modifier & Continuer  
 Le tableau suivant répertorie les tâches de débogage relatives à la fonction Modifier & Continuer et pointe vers leurs pages d'aide associées.  
  
|||  
|-|-|  
|Pour|Consultez|  
|Activer et désactiver la fonction Modifier & Continuer.|[Comment : activer et désactiver Modifier & Continuer](../Topic/How%20to:%20Enable%20and%20Disable%20Edit%20and%20Continue.md)|  
|Arrêter l'application des modifications au code par la fonction Modifier & Continuer.|[Comment : arrêter des modifications de code](../Topic/How%20to:%20Stop%20Code%20Changes.md)|  
|Appliquer les modifications en mode arrêt.|[Comment : appliquer des modifications en mode arrêt à l'aide de la fonctionnalité Modifier & Continuer](../Topic/How%20to:%20Apply%20Edits%20in%20Break%20Mode%20with%20Edit%20and%20Continue.md)|  
  
## Examiner les données de débogage  
 Le tableau suivant répertorie les tâches de débogage relatives à l'affichage des données de débogage et pointe vers leurs pages d'aide associées.  
  
|||  
|-|-|  
|Pour|Consultez|  
|Utiliser la fenêtre **Registres** pour afficher le contenu du registre.|[Comment : utiliser la fenêtre Registres](../Topic/How%20to:%20Use%20the%20Registers%20Window.md)|  
|Utiliser la fenêtre **Pile des appels** pour afficher les appels de fonctions ou de procédures actuellement dans la pile.|[Comment : utiliser la fenêtre Pile des appels](../Topic/How%20to:%20Use%20the%20Call%20Stack%20Window.md)|  
|Utiliser la fenêtre **Code Machine** pour afficher le code assembleur correspondant aux instructions créées par le compilateur.|[Comment : utiliser la fenêtre Code Machine](../Topic/How%20to:%20Use%20the%20Disassembly%20Window.md)|  
|Utiliser la fenêtre **Modules** pour répertorier et décrire les modules utilisés par votre programme.|[Comment : utiliser la fenêtre Modules](../Topic/How%20to:%20Use%20the%20Modules%20Window.md)|  
|Utilisez la fenêtre **Explorateur de scripts** pour répertorier les fichiers de script actuellement chargés dans le programme.|[Comment : afficher les documents de script](../Topic/How%20to:%20View%20Script%20Documents.md)|  
|Utiliser la fenêtre **Threads** pour examiner et contrôler les threads dans le programme.|[Comment : utiliser la fenêtre Threads](../Topic/How%20to:%20Use%20the%20Threads%20Window.md)|  
  
## Voir aussi  
 [Procédure pas à pas : débogage d'un Windows Form](../Topic/Walkthrough:%20Debugging%20a%20Windows%20Form.md)   
 [Débogage du code managé](/visual-studio/debugger/debugging-managed-code)   
 [Débogage du code natif](/visual-studio/debugger/debugging-native-code)   
 [Débogage d'applications et de scripts Web](/visual-studio/debugger/debugging-web-applications-and-script)   
 [Référence du débogage de l'interface utilisateur](/visual-studio/debugger/debugging-user-interface-reference)   
 [Paramètres et préparation du débogage](/visual-studio/debugger/debugger-settings-and-preparation)   
 [Principes de base du débogueur](/visual-studio/debugger/debugger-basics)   
 [Naviguer dans le code avec le débogueur](/visual-studio/debugger/navigating-through-code-with-the-debugger)   
 [Utilisation d'IntelliTrace](/visual-studio/debugger/intellitrace)   
 [Types de projets C\#, F\# et Visual Basic](../Topic/Debugging%20Preparation:%20C%23,%20F%23,%20and%20Visual%20Basic%20Project%20Types.md)   
 [Comment : appliquer des modifications en mode arrêt à l'aide de la fonctionnalité Modifier & Continuer](../Topic/How%20to:%20Apply%20Edits%20in%20Break%20Mode%20with%20Edit%20and%20Continue.md)