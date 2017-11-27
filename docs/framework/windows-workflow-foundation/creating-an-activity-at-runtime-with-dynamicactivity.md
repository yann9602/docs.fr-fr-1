---
title: "Création d'une activité en cours d'exécution avec DynamicActivity"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1af85cc6-912d-449e-90c5-c5db3eca5ace
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c984d235521a86c9657630d7ace3341c68f806ec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="creating-an-activity-at-runtime-with-dynamicactivity"></a>Création d'une activité en cours d'exécution avec DynamicActivity
<xref:System.Activities.DynamicActivity> est une classe concrète et scellée avec un constructeur public. <xref:System.Activities.DynamicActivity> peut servir à assembler les fonctionnalités d'activité au moment de l'exécution à l'aide d'un DOM d'activité.  
  
## <a name="dynamicactivity-features"></a>Fonctionnalités DynamicActivity  
 L'objet <xref:System.Activities.DynamicActivity> a accès aux propriétés d'exécution et aux arguments et variables, mais pas aux services d'exécution comme la planification d'activités enfants ou le suivi.  
  
 Les propriétés de niveau supérieur peuvent être définies à l'aide des objets <xref:System.Activities.Argument> du flux de travail. En code impératif, ces arguments sont créés à l'aide de propriétés CLR sur un nouveau type. En XAML, ils sont déclarés à l'aide de balises `x:Class` et `x:Member`.  
  
 Les activités sont générées à l'aide de l'interface <xref:System.Activities.DynamicActivity> avec le concepteur utilisant l'objet <xref:System.ComponentModel.ICustomTypeDescriptor>. Les activités créées dans le concepteur peuvent être chargées dynamiquement à l'aide de la méthode <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A>, comme le montre la procédure suivante.  
  
#### <a name="to-create-an-activity-at-runtime-using-imperative-code"></a>Pour créer une activité au moment de l'exécution à l'aide du code impératif  
  
1.  Ouvrez [!INCLUDE[vs2010](../../../includes/vs2010-md.md)].  
  
2.  Sélectionnez **fichier**, **nouveau**, **projet**. Sélectionnez **Workflow 4.0** sous **Visual C#** dans les **Types de projets** , puis sélectionnez le **v2010** nœud. Sélectionnez **Application Console de Workflow séquentiel** dans les **modèles** fenêtre. Nommez le nouveau projet « DynamicActivitySample ».  
  
3.  Cliquez sur Workflow1.xaml dans le projet HelloActivity et sélectionnez **supprimer**.  
  
4.  Ouvrez Program.cs. Ajoutez la directive suivante en début de fichier.  
  
    ```  
    using System.Collections.Generic;  
    ```  
  
5.  Remplacez le contenu de la méthode `Main` par le code ci-dessous. Ce dernier crée une activité <xref:System.Activities.Statements.Sequence> qui contient une activité <xref:System.Activities.Statements.WriteLine> unique et l'affecte à la propriété <xref:System.Activities.DynamicActivity.Implementation%2A> d'une nouvelle activité dynamique.  
  
    ```csharp  
    //Define the input argument for the activity  
    var textOut = new InArgument<string>();  
    //Create the activity, property, and implementation  
                Activity dynamicWorkflow = new DynamicActivity()  
                {  
                    Properties =   
                    {  
                        new DynamicActivityProperty  
                        {  
                            Name = "Text",  
                            Type = typeof(InArgument<String>),  
                            Value = textOut  
                        }  
                    },  
                    Implementation = () => new Sequence()  
                    {  
                        Activities =   
                        {  
                            new WriteLine()  
                            {  
                                Text = new InArgument<string>(env => textOut.Get(env))  
                            }  
                        }  
                    }  
                };  
    //Execute the activity with a parameter dictionary  
                WorkflowInvoker.Invoke(dynamicWorkflow, new Dictionary<string, object> { { "Text", "Hello World!" } });  
                Console.ReadLine();  
    ```  
  
6.  Exécutez l'application. Une fenêtre de console avec le texte « Hello World ! » affiche.  
  
#### <a name="to-create-an-activity-at-runtime-using-xaml"></a>Pour créer une activité au moment de l'exécution à l'aide de XAML  
  
1.  Ouvrez [!INCLUDE[vs2010](../../../includes/vs2010-md.md)].  
  
2.  Sélectionnez **fichier**, **nouveau**, **projet**. Sélectionnez **Workflow 4.0** sous **Visual C#** dans les **Types de projets** , puis sélectionnez le **v2010** nœud. Sélectionnez **Application Console de Workflow** dans les **modèles** fenêtre. Nommez le nouveau projet « DynamicActivitySample ».  
  
3.  Dans le projet HelloActivity, ouvrez Workflow1.xaml. Cliquez sur le **Arguments** option au bas du concepteur. Créez un argument `In` appelé `TextToWrite` de type `String`.  
  
4.  Faites glisser un **WriteLine** activité à partir de la **Primitives** section de la boîte à outils vers l’aire du concepteur. Affectez la valeur `TextToWrite` à la **texte** propriété de l’activité.  
  
5.  Ouvrez Program.cs. Ajoutez la directive suivante en début de fichier.  
  
    ```  
    using System.Activities.XamlIntegration;  
    ```  
  
6.  Remplacez le contenu de la méthode `Main` par le code suivant :  
  
    ```  
    Activity act2 = ActivityXamlServices.Load(@"Workflow1.xaml");  
                    results = WorkflowInvoker.Invoke(act2, new Dictionary<string, object> { { "TextToWrite", "HelloWorld!" } });  
    Console.ReadLine();  
    ```  
  
7.  Exécutez l'application. Une fenêtre de console avec le texte « Hello World ! » s’affiche.  
  
8.  Cliquez sur le fichier Workflow1.xaml dans le **l’Explorateur de solutions** et sélectionnez **afficher le Code**. Notez que la classe d'activité est créée avec `x:Class` et que la propriété est créée avec `x:Property`.  
  
## <a name="see-also"></a>Voir aussi  
 [Création de workflows, d’activités et d’expressions à l’aide du code impératif](../../../docs/framework/windows-workflow-foundation/authoring-workflows-activities-and-expressions-using-imperative-code.md)  
 [Création avec DynamicActivity](../../../docs/framework/windows-workflow-foundation/samples/dynamicactivity-creation.md)
