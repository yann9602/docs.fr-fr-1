---
title: "Intégration de WPF et WF en XAML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a4f53b48-fc90-4315-bca0-ba009562f488
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a8b6b10fbd9815280f8dcbb1d061363bef544a29
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="wpf-and-wf-integration-in-xaml"></a>Intégration de WPF et WF en XAML
Cet exemple montre comment créer une application qui utilise les fonctionnalités [!INCLUDE[avalon1](../../../../includes/avalon1-md.md)] et [!INCLUDE[wf](../../../../includes/wf-md.md)] dans un document XAML unique. Pour ce faire, l'exemple utilise [!INCLUDE[wf](../../../../includes/wf-md.md)] et l'extensibilité XAML.  
  
## <a name="sample-details"></a>Détails de l'exemple  
 Le fichier ShowWindow.xaml désérialise dans une activité <xref:System.Activities.Statements.Sequence> avec deux variables String manipulées par les activités de la séquence : `ShowWindow` et `WriteLine`. L'activité <xref:System.Activities.Statements.WriteLine> renvoie dans la fenêtre de console l'expression qu'elle assigne à la propriété <xref:System.Activities.Statements.WriteLine.Text%2A>. L'activité `ShowWindow` affiche une fenêtre [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] dans le cadre de sa logique d'exécution. Le <xref:System.Activities.ActivityContext.DataContext%2A> de la fenêtre inclut les variables déclarées dans la séquence. Les contrôles de la fenêtre déclarée dans l'activité `ShowWindow` utilisent la liaison de données pour manipuler ces variables. Enfin, la fenêtre contient un contrôle bouton. L'événement `Click` pour le bouton est géré par <xref:System.Activities.ActivityDelegate> nommé `MarkupExtension` qui contient une activité `CloseWindow`. `MarkUpExtension` appelle l'activité contenue qui fournit, comme contexte, tous les objets identifiés par `x:Name`, ainsi que le <xref:System.Activities.ActivityContext.DataContext%2A> de la fenêtre. Ainsi, le `CloseWindow.InArgument<Window>` peut être lié à l'aide d'une expression qui référence le nom de la fenêtre.  
  
 L'activité `ShowWindow` dérive de la classe <xref:System.Activities.AsyncCodeActivity%601> pour afficher une fenêtre [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] et se termine lorsque la fenêtre est fermée. La propriété `Window` est de type `Func<Window>` qui autorise la création de la fenêtre à la demande pour chaque exécution de l'activité. La propriété `Window` utilise un <xref:System.Xaml.XamlDeferringLoader> pour activer ce modèle d'évaluation différé. Le `FuncFactoryDeferringLoader` permet la capture d'un `XamlReader` pendant la sérialisation, puis sa lecture pendant l'exécution de l'activité.  
  
 Une activité bien écrite ne bloque jamais le thread de planificateur. Toutefois, l'activité `ShowWindow` ne peut pas se terminer tant que la fenêtre qu'elle affiche n'est pas fermée. L'activité `ShowWindow` parvient à ce comportement en dérivant de <xref:System.Activities.AsyncCodeActivity>, en appelant la méthode <xref:System.Activities.WorkflowInvoker.BeginInvoke%2A> dans la méthode <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> et en affichant la fenêtre de façon modale. Le délégué est appelé via le <xref:System.ServiceModel.InstanceContext.SynchronizationContext%2A> WPF. L'activité `ShowWindow` assigne la propriété <xref:System.Activities.ActivityContext.DataContext%2A> à la propriété `Window.DataContext` pour fournir un accès des contrôles liés aux données aux variables dans la portée.  
  
 Le dernier point intéressant dans cet exemple est un <xref:System.Workflow.ComponentModel.Serialization.MarkupExtension> appelé `DelegateActivityExtension`. La méthode `ProvideValue` de cette extension de balisage retourne un délégué qui appelle une activité incorporée. Cette activité s'exécute dans un environnement qui inclut le contexte des données [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] et toutes les valeurs `x:Name` dans la portée. Dans la méthode `GenericInvoke`, cet environnement est fourni à l'activité via une extension <xref:System.Activities.Hosting.SymbolResolver>. Cette extension est ajoutée à un <xref:System.Activities.WorkflowInvoker> utilisé ensuite pour appeler l'activité incorporée chaque fois que le délégué de l'extension de balisage est appelé.  
  
> [!NOTE]
>  Le concepteur par défaut ne prend pas en charge l'activité ShowWindow ; ainsi, le fichier ShowWindow.Xaml ne s'affiche pas correctement dans le concepteur.  
  
#### <a name="to-use-this-sample"></a>Pour utiliser cet exemple  
  
1.  À l'aide de [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], ouvrez le fichier solution WPFWFIntegration.sln.  
  
2.  Pour générer la solution, appuyez sur Ctrl+Maj+B.  
  
3.  Pour exécuter la solution, appuyez sur F5.  
  
4.  Tapez vos prénom et nom dans la boîte de dialogue.  
  
5.  Fermez la boîte de dialogue et la console répète votre nom.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\WPFWFIntegration`