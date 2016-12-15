---
title: "Overview of the Visual Basic Application Model | Microsoft Docs"
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
  - "My.Application object, Visual Basic application model"
  - "Visual Basic application model"
ms.assetid: 17538984-84fe-43c9-82c8-724c9529fe8b
caps.latest.revision: 30
caps.handback.revision: 30
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Overview of the Visual Basic Application Model
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] fournit un modèle précis pour contrôler le comportement des applications Windows Forms, à savoir le modèle d'application [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  Ce modèle inclut des événements pour gérer le démarrage et l'arrêt de l'application, ainsi que des événements pour l'interception des exceptions non gérées.  Il fournit également une prise en charge pour le développement des applications à instance unique.  Le modèle d'application est extensible, ce qui permet aux développeurs qui ont besoin de plus de contrôle de personnaliser ses méthodes substituables.  
  
## Utilisations du modèle d'application  
 Une application classique doit effectuer des tâches lorsqu'elle démarre et s'arrête.  Par exemple, lorsqu'elle démarre, l'application peut afficher un écran de démarrage, effectuer des connexions de base de données, charger un état enregistré, etc.  Lorsque l'application s'arrête, elle peut fermer des connexions de base de données, enregistrer l'état actuel, etc.  En outre, l'application peut exécuter du code spécifique lorsqu'elle s'arrête de manière inattendue, par exemple au cours d'une exception non gérée.  
  
 Le modèle d'application [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] facilite la création d'une application *à instance unique*.  Une application à instance unique est différente d'une application normale en ce sens qu'une seule instance de l'application peut être exécutée à la fois.  Lorsque vous essayez de lancer une autre instance d'une application à instance unique, l'instance initiale reçoit une notification \(par le biais de l'événement `StartupNextInstance`\) qu'une autre tentative de lancement a été effectuée.  La notification inclut les arguments de ligne de commande de l'instance suivante.  L'instance suivante de l'application est ensuite fermée avant qu'une initialisation ne se produise.  
  
 Une application à instance unique démarre et vérifie s'il s'agit de la première instance ou d'une instance suivante de l'application :  
  
-   S'il s'agit de la première instance, elle démarre comme d'habitude.  
  
-   Toute tentative ultérieure de démarrer l'application, alors que la première instance est en cours d'exécution, produit un comportement très différent.  La tentative suivante notifie la première instance à propos des arguments de ligne de commande, puis se ferme immédiatement.  La première instance gère l'événement `StartupNextInstance` pour déterminer la nature des arguments de ligne de commande, puis continue son exécution.  
  
     Ce diagramme montre comment une instance suivante signale la première instance.  
  
     ![Image Application à instance unique](../../../visual-basic/developing-apps/development-with-my/media/singleinstance.gif "SingleInstance")  
  
 En gérant l'événement `StartupNextInstance`, vous pouvez contrôler comment votre application à instance unique se comporte.  Par exemple, Microsoft Outlook s'exécute en général comme une application à instance unique. Lorsque Outlook est en cours d'exécution et que vous essayez de le redémarrer, le focus passe à l'instance d'origine mais une autre instance ne s'ouvre pas.  
  
## Événements du modèle d'application  
 Les événements suivants figurent dans le modèle d'application :  
  
-   **Démarrage de l'application**.  L'application déclenche l'événement <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup> lorsqu'elle démarre.  En gérant cet événement, vous pouvez ajouter du code qui initialise l'application avant que le formulaire principal soit chargé.  L'événement `Startup` prévoit également l'annulation de l'exécution de l'application pendant cette phase du processus de démarrage.  
  
     Vous pouvez configurer l'application pour qu'elle affiche un écran de démarrage pendant l'exécution du code de démarrage de l'application.  Par défaut, le modèle d'application supprime l'écran de démarrage lorsque l'argument de ligne de commande `/nosplash` ou `-nosplash` est utilisé.  
  
-   **Applications à instance unique**.  L'événement <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance> est déclenché lorsqu'une instance ultérieure d'une application à instance unique démarre.  L'événement passe les arguments de ligne de commande de l'instance suivante.  
  
-   **Exceptions non gérées**.  Si l'application rencontre une exception non gérée, elle déclenche l'événement <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException>.  Le gestionnaire de cet événement peut examiner l'exception et déterminer s'il faut continuer l'exécution ou non.  
  
     L'événement `UnhandledException` n'est pas déclenché dans certains cas.  Pour plus d’informations, consultez <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException>.  
  
-   **Changements de connectivité du réseau**.  Si la disponibilité du réseau de l'ordinateur change, l'application déclenche l'événement <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged>.  
  
     L'événement `NetworkAvailabilityChanged` n'est pas déclenché dans certains cas.  Pour plus d’informations, consultez <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged>.  
  
-   **Arrêt de l'application**.  L'application fournit l'événement <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown> pour signaler à quel moment elle va s'arrêter.  Dans ce gestionnaire d'événements, vous pouvez vérifier que les opérations que votre application doit exécuter \(fermeture et enregistrement, par exemple\) sont terminées.  Vous pouvez configurer votre application pour qu'elle s'arrête en même temps que le formulaire principal ou uniquement lorsque tous les formulaires se ferment.  
  
## Disponibilité  
 Par défaut, le modèle d'application [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] est disponible pour les projets Windows Forms.  Si vous configurez l'application pour qu'elle utilise un objet de démarrage différent ou qu'elle démarre le code d'application avec un `Sub Main` personnalisé, cet objet ou classe devra éventuellement fournir une implémentation de la classe <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> pour utiliser le modèle d'application.  Pour plus d'informations sur la modification de l'objet de démarrage, consultez [Page Application, Concepteur de projets \(Visual Basic\)](/visual-studio/ide/reference/application-page-project-designer-visual-basic).  
  
## Voir aussi  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>   
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup>   
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance>   
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException>   
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown>   
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged>   
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>   
 [Extending the Visual Basic Application Model](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-visual-basic-application-model.md)