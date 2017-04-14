---
title: "Cr&#233;ation d&#39;une activit&#233; en cours d&#39;ex&#233;cution avec DynamicActivity | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1af85cc6-912d-449e-90c5-c5db3eca5ace
caps.latest.revision: 9
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 9
---
# Cr&#233;ation d&#39;une activit&#233; en cours d&#39;ex&#233;cution avec DynamicActivity
<xref:System.Activities.DynamicActivity> est une classe concrète et scellée avec un constructeur public.<xref:System.Activities.DynamicActivity> peut servir à assembler les fonctionnalités d'activité au moment de l'exécution à l'aide d'un DOM d'activité.  
  
## Fonctionnalités DynamicActivity  
 L'objet <xref:System.Activities.DynamicActivity> a accès aux propriétés d'exécution et aux arguments et variables, mais pas aux services d'exécution comme la planification d'activités enfants ou le suivi.  
  
 Les propriétés de niveau supérieur peuvent être définies à l'aide des objets <xref:System.Activities.Argument> du flux de travail.En code impératif, ces arguments sont créés à l'aide de propriétés CLR sur un nouveau type.En XAML, ils sont déclarés à l'aide de balises `x:Class` et `x:Member`.  
  
 Les activités sont générées à l'aide de l'interface <xref:System.Activities.DynamicActivity> avec le concepteur utilisant l'objet <xref:System.ComponentModel.ICustomTypeDescriptor>.Les activités créées dans le concepteur peuvent être chargées dynamiquement à l'aide de la méthode <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A>, comme le montre la procédure suivante.  
  
#### Pour créer une activité au moment de l'exécution à l'aide du code impératif  
  
1.  Ouvrez [!INCLUDE[vs2010](../../../includes/vs2010-md.md)].  
  
2.  Sélectionnez **Fichier**, **Nouveau**, puis **Projet**.Dans la fenêtre **Types de projets**, sous **Visual C\#**, sélectionnez **Workflow 4.0**, puis le nœud **v2010**.Dans la fenêtre **Modèles**, sélectionnez **Application console de workflow séquentiel**.Nommez le nouveau projet « DynamicActivitySample ».  
  
3.  Dans le projet HelloActivity, cliquez avec le bouton droit sur Workflow1.xaml et sélectionnez **Supprimer**.  
  
4.  Ouvrez Program.cs.Ajoutez la directive suivante en début de fichier :  
  
    ```  
    using System.Collections.Generic;  
    ```  
  
5.  Remplacez le contenu de la méthode `Main` par le code ci\-dessous. Ce dernier crée une activité <xref:System.Activities.Statements.Sequence> qui contient une activité <xref:System.Activities.Statements.WriteLine> unique et l'affecte à la propriété <xref:System.Activities.DynamicActivity.Implementation%2A> d'une nouvelle activité dynamique.  
  
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
  
6.  Exécutez l'application.Une fenêtre de console contenant le texte « Hello World \! » s'affiche.  
  
#### Pour créer une activité au moment de l'exécution à l'aide de XAML  
  
1.  Ouvrez [!INCLUDE[vs2010](../../../includes/vs2010-md.md)].  
  
2.  Sélectionnez **Fichier**, **Nouveau**, puis **Projet**.Dans la fenêtre **Types de projets**, sous **Visual C\#**, sélectionnez **Workflow 4.0**, puis le nœud **v2010**.Dans la fenêtre **Modèles**, sélectionnez **Application console de workflow**.Nommez le nouveau projet « DynamicActivitySample ».  
  
3.  Dans le projet HelloActivity, ouvrez Workflow1.xaml.En bas du concepteur, cliquez sur l'option **Arguments**.Créez un argument `In` appelé `TextToWrite` de type `String`.  
  
4.  Faites glisser une activité **WriteLine** de la section **Primitives** de la boîte à outils à l'aire du concepteur.Affectez la valeur `TextToWrite` à la propriété **Text** de l'activité.  
  
5.  Ouvrez Program.cs.Ajoutez la directive suivante en début de fichier.  
  
    ```  
    using System.Activities.XamlIntegration;  
    ```  
  
6.  Remplacez le contenu de la méthode `Main` par le code suivant :  
  
    ```  
    Activity act2 = ActivityXamlServices.Load(@"Workflow1.xaml");  
                    results = WorkflowInvoker.Invoke(act2, new Dictionary<string, object> { { "TextToWrite", "HelloWorld!" } });  
    Console.ReadLine();  
    ```  
  
7.  Exécutez l'application.Une fenêtre de console contenant le texte « Hello World \! » apparaît.  
  
8.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur le fichier Workflow1.xaml et sélectionnez **Afficher le code**.Notez que la classe d'activité est créée avec `x:Class` et que la propriété est créée avec `x:Property`.  
  
## Voir aussi  
 [Création de workflows, d'activités et d'expressions à l'aide du code impératif](../../../docs/framework/windows-workflow-foundation//authoring-workflows-activities-and-expressions-using-imperative-code.md)   
 [Création avec DynamicActivity](../../../docs/framework/windows-workflow-foundation/samples/dynamicactivity-creation.md)