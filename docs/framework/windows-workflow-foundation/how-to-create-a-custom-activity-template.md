---
title: "Proc&#233;dure&#160;: cr&#233;er un mod&#232;le d&#39;activit&#233; personnalis&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6760a5cc-6eb8-465f-b4fa-f89b39539429
caps.latest.revision: 4
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# Proc&#233;dure&#160;: cr&#233;er un mod&#232;le d&#39;activit&#233; personnalis&#233;
Les modèles d'activité personnalisés sont utilisés pour personnaliser la configuration des activités, parmi lesquelles les activités composites personnalisées, afin que les utilisateurs n'aient pas besoin de créer individuellement chaque activité et de configurer manuellement leurs propriétés et les autres paramètres.Ces modèles personnalisés peuvent être rendus disponibles dans la **Boîte à outils** sur [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] ou à partir d'un concepteur réhébergé, dans lequel les utilisateurs peuvent les faire glisser sur l'aire de conception préconfigurée.[!INCLUDE[wfd2](../../../includes/wfd2-md.md)] est fourni avec des bons exemples de ces modèles : [Concepteur de modèles SendAndReceiveReply](../Topic/SendAndReceiveReply%20Template%20Designer.md) et [Concepteur de modèles ReceiveAndSendReply](../Topic/ReceiveAndSendReply%20Template%20Designer.md) dans la catégorie [Concepteurs d'activités de messagerie](../Topic/Messaging%20Activity%20Designers.md).  
  
 La première procédure dans cette rubrique explique comment créer un modèle d'activité personnalisé pour une activité **Delay**, et la deuxième procédure explique brièvement comment le rendre disponible dans un [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] pour vérifier que le modèle personnalisé fonctionne.  
  
 Les modèles d'activité personnalisés doivent implémenter l'<xref:System.Activities.Presentation.IActivityTemplateFactory>.L'interface dispose d'une seule méthode <xref:System.Activities.Presentation.IActivityTemplateFactory.Create%2A> avec laquelle vous pouvez créer et configurer les instances d'activité utilisées dans le modèle.  
  
### Pour créer un modèle pour l'activité Delay  
  
1.  Démarrez [!INCLUDE[vs2010](../../../includes/vs2010-md.md)].  
  
2.  Dans le menu **Fichier**, pointez sur **Nouveau**, puis sélectionnez **Projet**.  
  
     La boîte de dialogue **Nouveau projet** s'affiche.  
  
3.  Dans le volet **Types de projet**, sélectionnez **Workflow** dans les projets **Visual C\#** ou les regroupements **Visual Basic**, en fonction du langage choisi.  
  
4.  Dans le volet **Modèles**, sélectionnez **Bibliothèque d'activités**.  
  
5.  Dans la zone **Nom**, entrez `DelayActivityTemplate`.  
  
6.  Acceptez les valeurs par défaut dans les zones de texte **Emplacement** et **Nom de la solution**, puis cliquez sur **OK**.  
  
7.  Cliquez avec le bouton droit sur le répertoire References du projet DelayActivityTemplate dans l'**Explorateur de solutions**, puis choisissez **Ajouter une référence** pour ouvrir la boîte de dialogue **Ajouter une référence**.  
  
8.  Accédez à l'onglet **.NET**, sélectionnez **PresentationFramework** dans la colonne **Nom du composant** située à la gauche, puis cliquez sur **OK** pour ajouter une référence au fichier PresentationFramework.dll.  
  
9. Répétez cette procédure pour ajouter des références aux fichiers System.Activities.Presentation.dll et WindowsBase.dll.  
  
10. Cliquez avec le bouton droit sur le projet DelayActivityTemplate dans l'**Explorateur de solutions** et choisissez **Ajouter**, puis **Nouvel élément** pour ouvrir la boîte de dialogue **Ajouter un nouvel élément**.  
  
11. Sélectionnez le modèle **Classe**, nommez\-le MyDelayTemplate, puis cliquez sur **OK**.  
  
12. Ouvrez le fichier MyDelayTemplate.cs et ajoutez les instructions suivantes.  
  
    ```  
  
    //Namespaces added  
    using System.Activities;  
    using System.Activities.Statements;  
    using System.Activities.Presentation;  
    using System.Windows;  
  
    ```  
  
13. Implémentez <xref:System.Activities.Presentation.IActivityTemplateFactory> avec la classe `MyDelayActivity` dans le code suivant.Cela configure une durée de 10 secondes comme délai.  
  
    ```  
  
    public sealed class MyDelayActivity : IActivityTemplateFactory  
    {  
        public Activity Create(System.Windows.DependencyObject target)  
        {  
            return new System.Activities.Statements.Delay  
            {  
                DisplayName = "DelayActivityTemplate",  
                Duration = new TimeSpan(0, 0, 10)  
  
            };  
        }  
    }  
  
    ```  
  
14. Sélectionnez **Générer la solution** dans le menu **Générer** pour générer le fichier DelayActivityTemplate.dll.  
  
### Pour rendre le modèle disponible dans un concepteur de workflow  
  
1.  Cliquez avec le bouton droit sur la solution DelayActivityTemplate dans l'**Explorateur de solutions** et choisissez **Ajouter**, puis **Nouvel projet** pour ouvrir la boîte de dialogue **Ajouter un nouveau projet**.  
  
2.  Sélectionnez le modèle **Application console de workflow**, nommez\-le `CustomActivityTemplateApp`, puis cliquez sur **OK**.  
  
3.  Cliquez avec le bouton droit sur le répertoire References du projet CustomActivityTemplateApp dans l'**Explorateur de solutions**, puis choisissez **Ajouter une référence** pour ouvrir la boîte de dialogue **Ajouter une référence**.  
  
4.  Accédez à l'onglet **Projets**, sélectionnez **DelayActivityTemplate** dans la colonne **Nom du projet** située à gauche, puis cliquez sur **OK** pour ajouter une référence au fichier DelayActivityTemplate.dll que vous avez créé dans la première procédure.  
  
5.  Cliquez avec le bouton droit sur le projet CustomActivityTemplateApp dans l'**Explorateur de solutions**, puis choisissez **Générer** pour compiler l'application.  
  
6.  Cliquez avec le bouton droit sur le projet CustomActivityTemplateApp dans l'**Explorateur de solutions**, puis choisissez **Définir comme projet de démarrage**.  
  
7.  Sélectionnez **Exécuter sans débogage** dans le menu **Déboguer**, puis appuyez sur n'importe quelle touche pour continuer lorsque vous y êtes invité dans la fenêtre cmd.exe.  
  
8.  Ouvrez le fichier Workflow1.xaml, puis ouvrez la **Boîte à outils**.  
  
9. Recherchez le modèle **MyDelayActivity** dans la catégorie **DelayActivityTemplate**.Faites\-le glisser vers l'aire de conception.Vérifiez, dans la fenêtre **Propriétés**, que la valeur définie pour la propriété `Duration` est de 10 secondes.  
  
## Exemple  
 Le fichier MyDelayActivity.cs doit contenir le code suivant.  
  
```  
  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
  
//Namespaces added  
using System.Activities;  
using System.Activities.Statements;  
using System.Activities.Presentation;  
using System.Windows;  
  
namespace DelayActivityTemplate  
{  
    public sealed class MyDelayActivity : IActivityTemplateFactory  
    {  
        public Activity Create(System.Windows.DependencyObject target)  
        {  
            return new System.Activities.Statements.Delay  
            {  
                DisplayName = "DelayActivityTemplate",  
                Duration = new TimeSpan(0, 0, 10)  
  
            };  
        }  
    }  
}  
  
```  
  
## Voir aussi  
 <xref:System.Activities.Presentation.IActivityTemplateFactory>   
 [Personnalisation de l'expérience de conception de workflow](../../../docs/framework/windows-workflow-foundation//customizing-the-workflow-design-experience.md)