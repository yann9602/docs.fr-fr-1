---
title: Classe de base NativeActivity
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 254a4c50-425b-426d-a32f-0f7234925bac
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 22c9557c53c15fef3ca8dee4a0f665d333c5ffe4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="nativeactivity-base-class"></a>Classe de base NativeActivity
<xref:System.Activities.NativeActivity> est une classe abstraite avec un constructeur protégé. Comme l'objet <xref:System.Activities.CodeActivity>, la classe <xref:System.Activities.NativeActivity> sert à écrire le comportement impératif en implémentant une méthode <xref:System.Activities.NativeActivity.Execute%2A>. Contrairement à l'objet <xref:System.Activities.CodeActivity>, la classe <xref:System.Activities.NativeActivity> a accès à toutes les fonctionnalités exposées de l'exécution du workflow, via l'objet <xref:System.Activities.NativeActivityContext> passé à la méthode <xref:System.Activities.NativeActivity.Execute%2A>.  
  
## <a name="using-nativeactivitycontext"></a>Utilisation de NativeActivityContext  
 Les fonctionnalités de l'exécution du workflow sont accessibles à partir de la méthode <xref:System.Activities.NativeActivity.Execute%2A> en utilisant les membres du paramètre `context`, de type <xref:System.Activities.NativeActivityContext>. Les fonctionnalités disponibles via <xref:System.Activities.NativeActivityContext> sont notamment :  
  
-   obtention et définition d'arguments et de variables ;  
  
-   planification d'activités enfants à l'aide de la méthode <xref:System.Activities.NativeActivityContext.ScheduleActivity%2A> ;  
  
-   abandon de l'exécution de l'activité à l'aide de la méthode <xref:System.Activities.NativeActivityContext.Abort%2A> ;  
  
-   annulation de l'exécution de l'enfant à l'aide des méthodes <xref:System.Activities.NativeActivityContext.CancelChild%2A> et <xref:System.Activities.NativeActivityContext.CancelChildren%2A> ;  
  
-   accès aux signets d'activité à l'aide de méthodes telles que <xref:System.Activities.NativeActivityContext.CreateBookmark%2A>, <xref:System.Activities.NativeActivityContext.RemoveBookmark%2A> et <xref:System.Activities.NativeActivityContext.ResumeBookmark%2A> ;  
  
-   Fonctionnalités de suivi personnalisées à l'aide de <xref:System.Activities.CodeActivityContext.Track%2A>.  
  
-   accès aux propriétés d'exécution et aux propriétés de valeur de l'activité à l'aide des méthodes <xref:System.Activities.CodeActivityContext.GetProperty%2A> et <xref:System.Activities.NativeActivityContext.GetValue%2A> ;  
  
-   planification d'actions et de fonctions de l'activité à l'aide des méthodes <xref:System.Activities.NativeActivityContext.ScheduleAction%2A> et <xref:System.Activities.NativeActivityContext.ScheduleFunc%2A>.  
  
#### <a name="to-create-a-custom-activity-that-inherits-from-nativeactivity"></a>Pour créer une activité personnalisée qui hérite de NativeActivity  
  
1.  Ouvrez [!INCLUDE[vs2010](../../../includes/vs2010-md.md)].  
  
2.  Sélectionnez **fichier**, **nouveau**, puis **projet**. Sélectionnez **Workflow 4.0** sous **Visual C#** dans les **Types de projets** , puis sélectionnez le **v2010** nœud. Sélectionnez **bibliothèque d’activités** dans les **modèles** fenêtre. Nommez le nouveau projet HelloActivity.  
  
3.  Cliquez sur Activity1.xaml dans le projet HelloActivity et sélectionnez **supprimer**.  
  
4.  Cliquez sur le projet HelloActivity et sélectionnez **ajouter**, puis **classe**. Nommez la nouvelle classe HelloActivity.cs.  
  
5.  Dans le fichier HelloActivity.cs, ajoutez les directives `using` suivantes.  
  
    ```csharp  
    using System.Activities;  
    using System.Activities.Statements;  
    ```  
  
6.  Faites en sorte que la nouvelle classe hérite de <xref:System.Activities.NativeActivity> en ajoutant une classe de base à la déclaration de classe.  
  
    ```csharp  
    class HelloActivity : NativeActivity  
    ```  
  
7.  Ajoutez des fonctionnalités à la classe en ajoutant une méthode <xref:System.Activities.NativeActivity.Execute%2A>.  
  
    ```csharp  
    protected override void Execute(NativeActivityContext context)  
    {  
        Console.WriteLine("Hello World!");  
    }  
    ```  
  
8.  Substituez la méthode <xref:System.Activities.NativeActivity.CacheMetadata%2A> et appelez la méthode Add appropriée pour permettre au runtime du workflow de connaître les variables, les arguments, les enfants et les délégués de l'activité personnalisée. Pour plus d'informations, consultez la classe <xref:System.Activities.NativeActivityMetadata>.  
  
9. Utilisez l'objet <xref:System.Activities.NativeActivityContext> pour planifier un signet. Pour plus d'informations sur la création, la planification et la reprise d'un signet, consultez <xref:System.Activities.WorkflowApplicationIdleEventArgs.Bookmarks%2A>.  
  
    ```  
    protected override void Execute(NativeActivityContext context)  
        {  
            // Create a Bookmark and wait for it to be resumed.  
            context.CreateBookmark(BookmarkName.Get(context),   
                new BookmarkCallback(OnResumeBookmark));  
        }  
    ```
