---
title: "Vue d’ensemble du modèle d’Application Visual Basic | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- My.Application object, Visual Basic application model
- Visual Basic application model
ms.assetid: 17538984-84fe-43c9-82c8-724c9529fe8b
caps.latest.revision: 30
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: 0925bb102c148480d82128b91cbf1762de24e7ec
ms.lasthandoff: 03/13/2017

---
# <a name="overview-of-the-visual-basic-application-model"></a>Vue d'ensemble du modèle d'application Visual Basic
[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]fournit un modèle précis pour contrôler le comportement des applications Windows Forms : le [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] modèle d’Application. Ce modèle inclut des événements pour de l’application démarrage et arrêt, ainsi que les événements pour l’interception des exceptions non gérées. Il fournit également la prise en charge pour le développement d’applications à instance unique. Le modèle d’application est extensible, afin que les développeurs nécessitant davantage de contrôle peuvent personnaliser ses méthodes substituables.  
  
## <a name="uses-for-the-application-model"></a>Utilise le modèle d’Application  
 Une application classique doit effectuer des tâches lorsqu’il démarre et s’arrête. Par exemple, lorsqu’il démarre, l’application peut afficher un écran de démarrage, établir des connexions de base de données, charger un état enregistré et ainsi de suite. Lorsque l’application s’arrête, il peut fermer des connexions de base de données, enregistrer l’état actuel et ainsi de suite. En outre, l’application peut exécuter un code spécifique lors de la fermeture de l’application vers le bas, tel que lors d’une exception non gérée.  
  
 Le [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] modèle d’Application facilite la création d’un *uniques* application. Une application à instance unique diffère d’une application normale qui peut exécuter qu’une seule instance de l’application à la fois. Essayez de lancer une autre instance d’une application à instance unique entraîne l’instance d’origine notifié — au moyen de la `StartupNextInstance` événement — une autre tentative de lancement a été effectuée. La notification inclut les arguments de ligne de commande de l’instance suivante. L’instance suivante de l’application est fermée avant d’effectuer toute initialisation.  
  
 Une application à instance unique démarre et vérifie s’il s’agit de la première instance ou une instance de l’application suivante :  
  
-   Si elle est la première instance, elle démarre comme d’habitude.  
  
-   Toute tentative ultérieure de démarrer l’application, tandis que la première instance s’exécute, entraîne un comportement très différent. La tentative suivante notifie la première instance sur les arguments de ligne de commande, puis quitte immédiatement. La première instance gère la `StartupNextInstance` événement afin de déterminer quelles étaient les arguments de ligne de commande de l’instance suivante et continue de s’exécuter.  
  
     Ce diagramme montre comment une instance suivante signale la première instance.  
  
     ![Single Instance Application Image](../../../visual-basic/developing-apps/development-with-my/media/singleinstance.gif "SingleInstance")  
  
 En gérant la `StartupNextInstance` événement, vous pouvez contrôler le comportement de votre application à instance unique. Par exemple, Microsoft Outlook s’exécute généralement en tant qu’une application à instance unique ; Lorsque Outlook est en cours d’exécution et que vous essayez de démarrer Outlook, le focus se déplace vers l’instance d’origine mais une autre instance ne s’ouvre pas.  
  
## <a name="events-in-the-application-model"></a>Événements dans le modèle d’Application  
 Les événements suivants sont trouvent dans le modèle d’application :  
  
-   **Démarrage de l’application**. L’application déclenche le <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup>événement lors de son démarrage.</xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup> En gérant cet événement, vous pouvez ajouter du code qui initialise l’application avant de charger le formulaire principal. Le `Startup` événement prévoit également l’annulation de l’exécution de l’application pendant cette phase du processus de démarrage, si vous le souhaitez.  
  
     Vous pouvez configurer l’application pour afficher un écran de démarrage pendant l’exécution de code de démarrage de l’application. Par défaut, le modèle d’application supprime l’écran de démarrage lorsque l’écran soit le `/nosplash` ou `-nosplash` sert d’argument de ligne de commande.  
  
-   **Applications à instance unique**. Le <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance>événement est déclenché lorsqu’une instance suivante d’une application à instance unique démarre.</xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance> L’événement passe les arguments de ligne de commande de l’instance suivante.  
  
-   **Les exceptions non gérées**. Si l’application rencontre une exception non gérée, elle déclenche le <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException>événements.</xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> Votre gestionnaire pour cet événement peut examiner l’exception et déterminer s’il faut continuer l’exécution.  
  
     Le `UnhandledException` événement n’est pas déclenché dans certains cas. Pour plus d’informations, consultez <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException>.</xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException>  
  
-   **Changements de connectivité réseau**. Si la disponibilité du réseau de l’ordinateur change, l’application déclenche le <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged>événements.</xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged>  
  
     Le `NetworkAvailabilityChanged` événement n’est pas déclenché dans certains cas. Pour plus d’informations, consultez <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged>.</xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged>  
  
-   **Application arrêtée**. L’application fournit la <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown>événement pour signaler quand il est sur le point d’arrêt.</xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown> Dans ce cas gestionnaire, vous pouvez vous assurer que les opérations de votre application doivent effectuer, fermeture et l’enregistrement, par exemple, sont terminées. Vous pouvez configurer votre application s’arrête lorsque le formulaire principal, ou arrêter uniquement lorsque tous les formulaires se ferment.  
  
## <a name="availability"></a>Disponibilité  
 Par défaut, le [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] modèle d’Application est disponible pour les projets Windows Forms. Si vous configurez l’application pour utiliser un objet de démarrage différent, ou commencer le code d’application personnalisé `Sub Main`, cet objet ou classe devra éventuellement fournir une implémentation de la <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>classe à utiliser le modèle d’application.</xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> Pour plus d’informations sur la modification de l’objet de démarrage, consultez [Application Page, Project Designer (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/application-page-project-designer-visual-basic).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase></xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>   
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup></xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup>   
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance></xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance>   
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException></xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException>   
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown></xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown>   
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged></xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged>   
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase></xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>   
 [Extension du modèle d’application Visual Basic](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-visual-basic-application-model.md)
