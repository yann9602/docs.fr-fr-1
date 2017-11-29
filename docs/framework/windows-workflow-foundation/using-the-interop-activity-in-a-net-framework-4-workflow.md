---
title: "Utilisation de l'activité d'interopérabilité dans un flux de travail .NET Framework 4"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9bb747f0-eb33-4f70-84cd-317382372dcd
caps.latest.revision: "20"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c485a1c2c69169812e69c3bc1ea9969d12467d53
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="using-the-interop-activity-in-a-net-framework-4-workflow"></a>Utilisation de l'activité d'interopérabilité dans un flux de travail .NET Framework 4
Les activités créées à l'aide de [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] ou [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] peuvent être utilisées dans un flux de travail [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] en utilisant l'activité <xref:System.Activities.Statements.Interop>. Cette rubrique propose une vue d'ensemble de l'utilisation de l'activité <xref:System.Activities.Statements.Interop>.  
  
> [!NOTE]
>  Le <xref:System.Activities.Statements.Interop> n’apparaît pas dans la boîte à outils du Concepteur de flux de travail, sauf si les projets du flux de travail a son **Framework cible** défini sur **.Net Framework 4** ou version ultérieure.  
  
## <a name="using-the-interop-activity-in-net-framework-45-workflows"></a>Utilisation de l'activité Interop dans les flux de travail .NET Framework 4.5  
 Cette rubrique consiste à créer une bibliothèque d'activité [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] qui contient une activité `DiscountCalculator`. L'activité `DiscountCalculator` calcule une remise sur la base d'un montant d'achat et se compose d'un objet <xref:System.Workflow.Activities.SequenceActivity> qui contient un objet <xref:System.Workflow.Activities.PolicyActivity>.  
  
> [!NOTE]
>  L'activité [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] créée dans cette rubrique utilise un objet <xref:System.Workflow.Activities.PolicyActivity> pour implémenter la logique de l'activité. L'utilisation d'une activité [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] personnalisée ou de l'activité <xref:System.Activities.Statements.Interop> n'est pas obligatoire pour utiliser des règles dans un flux de travail [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]. Pour obtenir un exemple d’utilisation de règles dans un [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] workflow sans utiliser le <xref:System.Activities.Statements.Interop> activité, consultez le [activité de stratégie dans le .NET Framework 4.5](../../../docs/framework/windows-workflow-foundation/samples/policy-activity-in-net-framework-4-5.md) exemple.  
  
#### <a name="to-create-the-net-framework-35-activity-library-project"></a>Pour créer le projet de bibliothèque d'activités .NET Framework 3.5  
  
1.  Ouvrez [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] et sélectionnez **nouveau** , puis **projet...** à partir de la **fichier** menu.  
  
2.  Développez le **autres Types de projets** nœud dans le **modèles installés** volet et sélectionnez **Solutions Visual Studio**.  
  
3.  Sélectionnez **nouvelle Solution** à partir de la **Solutions Visual Studio** liste. Type `PolicyInteropDemo` dans les **nom** , puis cliquez sur **OK**.  
  
4.  Avec le bouton droit **PolicyInteropDemo** dans **l’Explorateur de solutions** et sélectionnez **ajouter** , puis **nouveau projet...** .  
  
    > [!TIP]
    >  Si le **l’Explorateur de solutions** fenêtre n’est pas visible, sélectionnez **l’Explorateur de solutions** à partir de la **vue** menu.  
  
5.  Dans le **modèles installés** liste, sélectionnez **Visual C#** , puis **Workflow**. Sélectionnez **.NET Framework 3.5** dans la liste déroulante de version du .NET Framework, puis sélectionnez **bibliothèque d’activités de flux de travail** à partir de la **modèles** liste.  
  
6.  Type `PolicyActivityLibrary` dans les **nom** , puis cliquez sur **OK**.  
  
7.  Avec le bouton droit **Activity1.cs** dans **l’Explorateur de solutions** et sélectionnez **supprimer**. Pour confirmer, cliquez sur **OK** .  
  
#### <a name="to-create-the-discountcalculator-activity"></a>Pour créer l'activité DiscountCalculator  
  
1.  Avec le bouton droit **PolicyActivityLibrary** dans **l’Explorateur de solutions** et sélectionnez **ajouter** , puis **activité en cours...** .  
  
2.  Sélectionnez **activité (avec séparation de code)** à partir de la **éléments Visual c#** liste. Type `DiscountCalculator` dans les **nom** , puis cliquez sur **OK**.  
  
3.  Avec le bouton droit **DiscountCalculator.xoml** dans **l’Explorateur de solutions** et sélectionnez **afficher le Code**.  
  
4.  Ajoutez les trois propriétés suivantes à la classe `DiscountCalculator` :  
  
    ```csharp  
    public partial class DiscountCalculator : SequenceActivity  
    {  
        public double Subtotal { get; set; }  
        public double DiscountPercent { get; set; }  
        public double Total { get; set; }  
    }  
    ```  
  
5.  Avec le bouton droit **DiscountCalculator.xoml** dans **l’Explorateur de solutions** et sélectionnez **Concepteur de vue**.  
  
6.  Faites glisser un **stratégie** activité à partir de la **Windows Workflow v3.0** section de la **boîte à outils** et déposez-la dans le **DiscountCalculator** activité .  
  
    > [!TIP]
    >  Si le **boîte à outils** fenêtre n’est pas visible, sélectionnez **boîte à outils** à partir de la **vue** menu.  
  
#### <a name="to-configure-the-rules"></a>Pour configurer les règles  
  
1.  Cliquez sur récemment ajouté **stratégie** activité pour la sélectionner, si elle n’est pas déjà sélectionnée.  
  
2.  Cliquez sur le **RuleSetReference** propriété dans le **propriétés** fenêtre pour la sélectionner, puis cliquez sur le bouton de sélection à droite de la propriété.  
  
    > [!TIP]
    >  Si le **propriétés** fenêtre n’est pas visible, choisissez **fenêtre Propriétés** à partir de la **vue** menu.  
  
3.  Sélectionnez **cliquez sur Nouveau...** .  
  
4.  Cliquez sur **ajouter une règle**.  
  
5.  Tapez l’expression suivante dans le **Condition** boîte.  
  
    ```  
    this.Subtotal >= 50 && this.Subtotal < 100  
    ```  
  
6.  Tapez l’expression suivante dans le **Actions Then** boîte.  
  
    ```  
    this.DiscountPercent = 0.075  
    ```  
  
7.  Cliquez sur **ajouter une règle**.  
  
8.  Tapez l’expression suivante dans le **Condition** boîte.  
  
    ```  
    this.Subtotal >= 100  
    ```  
  
9. Tapez l’expression suivante dans le **Actions Then** boîte.  
  
    ```  
    this.DiscountPercent = 0.15  
    ```  
  
10. Cliquez sur **ajouter une règle**.  
  
11. Tapez l’expression suivante dans le **Condition** boîte.  
  
    ```  
    this.DiscountPercent > 0  
    ```  
  
12. Tapez l’expression suivante dans le **Actions Then** boîte.  
  
    ```  
    this.Total = this.Subtotal - this.Subtotal * this.DiscountPercent  
    ```  
  
13. Tapez l’expression suivante dans le **Actions Else** boîte.  
  
    ```  
    this.Total = this.Subtotal  
    ```  
  
14. Cliquez sur **OK** pour fermer la **Éditeur d’ensemble de règles** boîte de dialogue.  
  
15. Vérifiez que le nouvellement créé <xref:System.Workflow.Activities.Rules.RuleSet> est sélectionné dans le **nom** liste, puis cliquez sur **OK**.  
  
16. Appuyez sur Ctrl+Maj+B pour générer la solution.  
  
 L'exemple de code suivant indique les règles ajoutées à l'activité `DiscountCalculator` lors de cette procédure.  
  
```  
Rule1: IF this.Subtotal >= 50 && this.Subtotal < 100   
       THEN this.DiscountPercent = 0.075   
  
Rule2: IF this. Subtotal >= 100   
       THEN this.DiscountPercent = 0.15   
  
Rule3: IF this.DiscountPercent > 0   
       THEN this.Total = this.Subtotal - this.Subtotal * this.DiscountPercent   
       ELSE this.Total = this.Subtotal  
```  
  
 Lors de l'exécution de l'objet <xref:System.Workflow.Activities.PolicyActivity>, ces trois règles évaluent et modifient les valeurs de propriété `Subtotal`, `DiscountPercent` et `Total` de l'activité `DiscountCalculator` pour calculer la remise souhaitée.  
  
## <a name="using-the-discountcalculator-activity-with-the-interop-activity"></a>Utilisation de l'activité DiscountCalculator avec l'activité Interop  
 Pour utiliser l'activité `DiscountCalculator` dans un flux de travail [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)], l'activité <xref:System.Activities.Statements.Interop> est utilisée. Dans cette section, deux flux de travail sont créés, l'un à l'aide du code et l'autre à l'aide du Workflow Designer. Ces flux de travail indiquent comment utiliser l'activité <xref:System.Activities.Statements.Interop> avec l'activité `DiscountCalculator`. La même application hôte est utilisée pour les deux flux de travail.  
  
#### <a name="to-create-the-host-application"></a>Pour créer l'application hôte  
  
1.  Avec le bouton droit **PolicyInteropDemo** dans **l’Explorateur de solutions** et sélectionnez **ajouter**, puis **nouveau projet...** .  
  
2.  Vérifiez que **.NET Framework 4.5** est sélectionné dans la liste déroulante de version du .NET Framework, puis sélectionnez **Application Console de Workflow** à partir de la **éléments Visual c#** liste.  
  
3.  Type `PolicyInteropHost` dans les **nom** , puis cliquez sur **OK**.  
  
4.  Avec le bouton droit **PolicyInteropHost** dans **l’Explorateur de solutions** et sélectionnez **propriétés**.  
  
5.  Dans le **framework cible** déroulante liste, modifiez la sélection à partir de **.NET Framework 4 Client Profile** à **.NET Framework 4.5**. Cliquez sur **Oui** pour confirmer.  
  
6.  Avec le bouton droit **PolicyInteropHost** dans **l’Explorateur de solutions** et sélectionnez **ajouter une référence...** .  
  
7.  Sélectionnez **PolicyActivityLibrary** à partir de la **projets** onglet et cliquez sur **OK**.  
  
8.  Avec le bouton droit **PolicyInteropHost** dans **l’Explorateur de solutions** et sélectionnez **ajouter une référence...** .  
  
9. Sélectionnez **sous**, **System.Workflow.ComponentModel**, puis **System.workflow.ComponentModel** à partir de la **.NET**onglet et cliquez sur **OK**.  
  
10. Avec le bouton droit **PolicyInteropHost** dans **l’Explorateur de solutions** et sélectionnez **définir comme projet de démarrage**.  
  
11. Appuyez sur Ctrl+Maj+B pour générer la solution.  
  
### <a name="using-the-interop-activity-in-code"></a>Utilisation de l'activité Interop dans le code  
 Dans cet exemple, une définition de flux de travail est créée à l'aide du code qui contient les activités <xref:System.Activities.Statements.Interop> et `DiscountCalculator`. Ce flux de travail est appelé à l'aide de l'objet <xref:System.Activities.WorkflowInvoker> et les résultats de l'évaluation de règle sont écrits dans la console à l'aide d'une activité <xref:System.Activities.Statements.WriteLine>.  
  
##### <a name="to-use-the-interop-activity-in-code"></a>Pour utiliser l'activité Interop dans le code  
  
1.  Avec le bouton droit **Program.cs** dans **l’Explorateur de solutions** et sélectionnez **afficher le Code**.  
  
2.  En tête du fichier, ajoutez l'instruction `using` suivante :  
  
    ```csharp  
    using PolicyActivityLibrary;  
    ```  
  
3.  Supprimez le contenu de la méthode `Main` et remplacez-le par le code suivant :  
  
    ```csharp  
    static void Main(string[] args)  
    {  
        CalculateDiscountUsingCodeWorkflow();  
    }  
    ```  
  
4.  Dans la classe `Program`, créez une méthode appelée `CalculateDiscountUsingCodeWorkflow` qui contient le code suivant :  
  
    ```csharp  
    static void CalculateDiscountUsingCodeWorkflow()  
    {  
        Variable<double> Subtotal = new Variable<double>  
        {  
            Default = 75.99,  
            Name = "Subtotal"  
        };  
  
        Variable<double> DiscountPercent = new Variable<double>  
        {  
            Name = "DiscountPercent"  
        };  
  
        Variable<double> Total = new Variable<double>  
        {  
            Name = "Total"  
        };  
  
        Activity wf = new Sequence  
        {  
            Variables = { Subtotal, DiscountPercent, Total },  
            Activities =   
            {  
                new Interop  
                {  
                    ActivityType = typeof(DiscountCalculator),  
                    ActivityProperties =   
                    {  
                        { "Subtotal", new InArgument<double>(Subtotal) },  
                        { "DiscountPercentOut", new OutArgument<double>(DiscountPercent) },  
                        { "TotalOut", new OutArgument<double>(Total) }  
                    }  
                },  
                new WriteLine  
                {  
                    Text =  new InArgument<string>(env =>   
                        string.Format("Subtotal: {0:C}, Discount {1}%, Total {2:C}",   
                        Subtotal.Get(env), DiscountPercent.Get(env) * 100, Total.Get(env)))  
                }  
            }  
        };  
  
        WorkflowInvoker.Invoke(wf);  
    }  
    ```  
  
    > [!NOTE]
    >  Les propriétés `Subtotal`, `DiscountPercent` et `Total` de l'activité `DiscountCalculator` sont signalées en tant qu'arguments de l'activité <xref:System.Activities.Statements.Interop> et liées à des variables de flux de travail locales dans la collection <xref:System.Activities.Statements.Interop> de l'activité <xref:System.Activities.Statements.Interop.ActivityProperties%2A>. `Subtotal` est ajouté en tant qu'argument <xref:System.Activities.ArgumentDirection.In>, car les données `Subtotal` sont diffusées dans l'activité <xref:System.Activities.Statements.Interop>, et `DiscountPercent` et `Total` sont ajoutés comme arguments <xref:System.Activities.ArgumentDirection.Out>, car leurs données sont diffusées hors de l'activité <xref:System.Activities.Statements.Interop>. Notez que les deux arguments <xref:System.Activities.ArgumentDirection.Out> sont ajoutés avec les noms `DiscountPercentOut` et `TotalOut` pour indiquer qu'ils représentent des arguments <xref:System.Activities.ArgumentDirection.Out>. Le type `DiscountCalculator` est spécifié comme l'objet <xref:System.Activities.Statements.Interop> de l'activité <xref:System.Activities.Statements.Interop.ActivityType%2A>.  
  
5.  Appuyez sur Ctrl+F5 pour générer et exécuter l'application. Remplacez la valeur `Subtotal` par des valeurs différentes pour tester les différents niveaux de remise fournis par l'activité `DiscountCalculator`.  
  
    ```csharp  
    Variable<double> Subtotal = new Variable<double>  
    {  
        Default = 75.99, // Change this value.  
        Name = "Subtotal"  
    };  
    ```  
  
### <a name="using-the-interop-activity-in-the-workflow-designer"></a>Utilisation de l'activité Interop dans le Workflow Designer  
 Dans cet exemple, un flux de travail est créé à l'aide du Workflow Designer. Ce flux de travail a les mêmes fonctionnalités que l'exemple précédent, sauf qu'au lieu d'utiliser une activité <xref:System.Activities.Statements.WriteLine> pour afficher la remise, l'application hôte récupère et affiche les informations de remise à la fin du flux de travail. De plus, au lieu d'une utilisation des variables de flux de travail locales pour contenir les données, les arguments sont créés dans le Workflow Designer et les valeurs sont passées à partir de l'hôte lors de l'appel du flux de travail.  
  
##### <a name="to-host-the-policyactivity-using-a-workflow-designer-created-workflow"></a>Pour héberger l'activité PolicyActivity à l'aide d'un flux de travail créé par le Workflow Designer  
  
1.  Avec le bouton droit **Workflow1.xaml** dans **l’Explorateur de solutions** et sélectionnez **supprimer**. Pour confirmer, cliquez sur **OK** .  
  
2.  Avec le bouton droit **PolicyInteropHost** dans **l’Explorateur de solutions** et sélectionnez **ajouter**, **un nouvel élément...** .  
  
3.  Développez le **éléments Visual c#** nœud et sélectionnez **Workflow**. Sélectionnez **activité** à partir de la **éléments Visual c#** liste.  
  
4.  Type `DiscountWorkflow` dans les **nom** , puis cliquez sur **ajouter**.  
  
5.  Cliquez sur le **Arguments** bouton sur le côté inférieur gauche du Concepteur de flux de travail pour afficher la **Arguments** volet.  
  
6.  Cliquez sur **créer un Argument**.  
  
7.  Type `Subtotal` dans les **nom** boîte, sélectionnez **dans** à partir de la **Direction** liste déroulante, sélectionnez **Double** à partir de la **Type d’argument** liste déroulante, puis appuyez sur ENTRÉE pour enregistrer l’argument.  
  
    > [!NOTE]
    >  Si **Double** ne figure pas dans le **type d’Argument** la liste déroulante, sélectionnez **rechercher des Types...** , type `System.Double` dans les **nom de Type** , puis cliquez sur **OK**.  
  
8.  Cliquez sur **créer un Argument**.  
  
9. Type `DiscountPercent` dans les **nom** boîte, sélectionnez **hors** à partir de la **Direction** liste déroulante, sélectionnez **Double** à partir de la **Type d’argument** liste déroulante, puis appuyez sur ENTRÉE pour enregistrer l’argument.  
  
10. Cliquez sur **créer un Argument**.  
  
11. Type `Total` dans les **nom** boîte, sélectionnez **hors** à partir de la **Direction** liste déroulante, sélectionnez **Double** à partir de la **Type d’argument** liste déroulante, puis appuyez sur ENTRÉE pour enregistrer l’argument.  
  
12. Cliquez sur le **Arguments** bouton sur le côté inférieur gauche du Concepteur de flux de travail pour fermer la **Arguments** volet.  
  
13. Faites glisser un **séquence** activité à partir de la **flux de contrôle** section de la **boîte à outils** et déposez-le sur l’aire de conception de flux de travail.  
  
14. Faites glisser un **Interop** activité à partir de la **Migration** section de la **boîte à outils** et déposez-la dans le **séquence** activité.  
  
15. Cliquez sur le **Interop** activité sur le **cliquez pour parcourir...** étiquette, tapez **DiscountCalculator** dans les **nom de Type** , puis cliquez sur **OK**.  
  
    > [!NOTE]
    >  Lorsque l'activité <xref:System.Activities.Statements.Interop> est ajoutée au flux de travail et que le type `DiscountCalculator` est spécifié comme sa propriété <xref:System.Activities.Statements.Interop.ActivityType%2A>, l'activité <xref:System.Activities.Statements.Interop> expose trois arguments <xref:System.Activities.ArgumentDirection.In> et trois arguments <xref:System.Activities.ArgumentDirection.Out> qui représentent les trois propriétés publiques de l'activité `DiscountCalculator`. Le <xref:System.Activities.ArgumentDirection.In> arguments ont le même nom que les trois propriétés publiques et les trois <xref:System.Activities.ArgumentDirection.Out> arguments ont les mêmes noms avec **hors** ajouté au nom de propriété. Dans les étapes suivantes, les arguments de flux de travail créés dans les étapes précédentes sont liés aux arguments de l'activité <xref:System.Activities.Statements.Interop>.  
  
16. Type `DiscountPercent` dans les **entrer une expression VB** zone située à droite de la **DiscountPercentOut** propriété et appuyez sur TAB.  
  
17. Type `Subtotal` dans les **entrer une expression VB** zone située à droite de la **sous-total** propriété et appuyez sur TAB.  
  
18. Type `Total` dans les **entrer une expression VB** zone située à droite de la **TotalOut** propriété et appuyez sur TAB.  
  
19. Avec le bouton droit **Program.cs** dans **l’Explorateur de solutions** et sélectionnez **afficher le Code**.  
  
20. En tête du fichier, ajoutez l'instruction `using` suivante :  
  
    ```csharp  
    using System.Collections.Generic;  
    ```  
  
21. Supprimez l'appel à la méthode `CalculateDiscountInCode` dans la méthode `Main` et ajoutez le code suivant :  
  
    > [!NOTE]
    >  Si vous n'avez pas suivi la procédure précédente et si le code `Main` par défaut est présent, remplacez le contenu de `Main` par le code suivant :  
  
    ```csharp  
    static void Main(string[] args)  
    {  
        CalculateDiscountUsingDesignerWorkflow();  
        //CalculateDiscountUsingCodeWorkflow();  
    }  
    ```  
  
22. Dans la classe `Program`, créez une méthode appelée `CalculateDiscountUsingDesignerWorkflow` qui contient le code suivant :  
  
    ```csharp  
    static void CalculateDiscountUsingDesignerWorkflow()  
    {  
        double SubtotalValue = 125.99;  
        Dictionary<string, object> wfargs = new Dictionary<string, object>  
        {  
            {"Subtotal", SubtotalValue}  
        };  
  
        Activity wf = new DiscountWorkflow();  
  
        IDictionary<string, object> outputs =  
            WorkflowInvoker.Invoke(wf, wfargs);  
  
        Console.WriteLine("Subtotal: {0:C}, Discount {1}%, Total {2:C}",  
            SubtotalValue, (double)outputs["DiscountPercent"] * 100,  
            outputs["Total"]);  
    }  
    ```  
  
23. Appuyez sur Ctrl+F5 pour générer et exécuter l'application. Pour spécifier un montant `Subtotal` différent, modifiez la valeur de `SubtotalValue` dans le code suivant :  
  
    ```csharp  
    double SubtotalValue = 125.99; // Change this value.  
    ```  
  
## <a name="rules-features-overview"></a>Vue d'ensemble des fonctionnalités des règles  
 Le moteur de règles [!INCLUDE[wf1](../../../includes/wf1-md.md)] fournit un support pour le traitement des règles dans l'ordre de priorité à l'aide du chaînage avant. Les règles peuvent être évaluées pour un seul élément ou pour les éléments d'une collection. Pour obtenir une vue d'ensemble des règles, ainsi que des informations sur des fonctionnalités particulières des règles, veuillez vous reporter au tableau suivant :  
  
|Fonctionnalité des règles|Documentation|  
|-------------------|-------------------|  
|Vue d'ensemble des règles|[Présentation du moteur de règles Windows Workflow Foundation](http://go.microsoft.com/fwlink/?LinkID=152836)|  
|RuleSet|[À l’aide de groupes de règles dans les Workflows](http://go.microsoft.com/fwlink/?LinkId=178516) et<xref:System.Workflow.Activities.Rules.RuleSet>|  
|Évaluation des règles|[Évaluation des règles dans les ensembles de règles](http://go.microsoft.com/fwlink/?LinkId=178517)|  
|Chaînage des règles|[Contrôle de chaînage avant](http://go.microsoft.com/fwlink/?LinkId=178518) et [chaînage avant des règles](http://go.microsoft.com/fwlink/?LinkId=178519)|  
|Traitement des collections dans les règles|[Collections dans les règles de traitement](http://go.microsoft.com/fwlink/?LinkId=178520)|  
|Utilisation de l'activité PolicyActivity|[À l’aide de l’activité PolicyActivity](http://go.microsoft.com/fwlink/?LinkId=178521) et<xref:System.Workflow.Activities.PolicyActivity>|  
  
 Les flux de travail créés dans [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] n'utilisent pas toutes les fonctionnalités de règles fournies par [!INCLUDE[wf1](../../../includes/wf1-md.md)], telles que les conditions d'activité déclaratives et les activités conditionnelles comme <xref:System.Workflow.Activities.ConditionedActivityGroup> et <xref:System.Workflow.Activities.ReplicatorActivity>. Si nécessaire, ces fonctionnalités sont disponibles pour les flux de travail créés à l'aide de [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] et [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)]. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Conseils de migration](../../../docs/framework/windows-workflow-foundation/migration-guidance.md).
