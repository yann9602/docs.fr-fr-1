---
title: "Création de l'activité de workflow à l'aide de la classe CodeActivity"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cfe315c1-f86d-43ec-b9ce-2f8c469b1106
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2daec260c1224cd81280c6bf699b70efc2072588
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="workflow-activity-authoring-using-the-codeactivity-class"></a>Création de l'activité de workflow à l'aide de la classe CodeActivity
Les activités créées en héritant de <xref:System.Activities.CodeActivity> peuvent implémenter un comportement impératif de base en remplaçant la méthode <xref:System.Activities.CodeActivity.Execute%2A>.  
  
## <a name="using-codeactivitycontext"></a>Utilisation de CodeActivityContext  
 Les fonctionnalités de l'exécution du workflow sont accessibles à partir de la méthode <xref:System.Activities.CodeActivity.Execute%2A> en utilisant les membres du paramètre `context`, de type <xref:System.Activities.CodeActivityContext>. Les fonctionnalités disponibles via <xref:System.Activities.CodeActivityContext> sont notamment :  
  
-   Obtention et définition des valeurs de variables et d'arguments.  
  
-   Fonctionnalités de suivi personnalisées à l'aide de <xref:System.Activities.CodeActivityContext.Track%2A>.  
  
-   Accès aux propriétés d'exécution de l'activité à l'aide de <xref:System.Activities.CodeActivityContext.GetProperty%2A>.  
  
#### <a name="to-create-a-custom-activity-that-inherits-from-codeactivity"></a>Pour créer une activité personnalisée qui hérite de CodeActivity  
  
1.  Ouvrez [!INCLUDE[vs2010](../../../includes/vs2010-md.md)].  
  
2.  Sélectionnez **fichier**, **nouveau**, puis **projet**. Sélectionnez **Workflow 4.0** sous **Visual C#** dans les **Types de projets** , puis sélectionnez le **v2010** nœud. Sélectionnez **bibliothèque d’activités** dans les **modèles** fenêtre. Nommez le nouveau projet HelloActivity.  
  
3.  Cliquez sur Activity1.xaml dans le projet HelloActivity et sélectionnez **supprimer**.  
  
4.  Cliquez sur le projet HelloActivity et sélectionnez **ajouter** , puis **classe**. Nommez la nouvelle classe HelloActivity.cs.  
  
5.  Dans le fichier HelloActivity.cs, ajoutez les directives `using` suivantes.  
  
    ```csharp  
    using System.Activities;  
    using System.Activities.Statements;  
    ```  
  
6.  Faites en sorte que la nouvelle classe hérite de <xref:System.Activities.CodeActivity> en ajoutant une classe de base à la déclaration de classe.  
  
    ```csharp  
    class HelloActivity : CodeActivity  
    ```  
  
7.  Ajoutez des fonctionnalités à la classe en ajoutant une méthode <xref:System.Activities.CodeActivity.Execute%2A>.  
  
    ```csharp  
    protected override void Execute(CodeActivityContext context)  
    {  
        Console.WriteLine("Hello World!");  
    }  
    ```  
  
8.  Utilisez le <xref:System.Activities.CodeActivityContext> pour créer un enregistrement de suivi.  
  
    ```csharp  
    protected override void Execute(CodeActivityContext context)  
    {  
        Console.WriteLine("Hello World!");  
        CustomTrackingRecord record = new CustomTrackingRecord("MyRecord");  
        record.Data.Add(new KeyValuePair<String, Object>("ExecutionTime", DateTime.Now));  
        context.Track(record);  
    }  
    ```
