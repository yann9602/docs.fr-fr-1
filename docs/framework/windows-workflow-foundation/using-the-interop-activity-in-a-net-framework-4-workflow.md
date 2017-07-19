---
title: "Utilisation de l&#39;activit&#233; d&#39;interop&#233;rabilit&#233; dans un flux de travail .NET Framework&#160;4 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9bb747f0-eb33-4f70-84cd-317382372dcd
caps.latest.revision: 20
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 20
---
# Utilisation de l&#39;activit&#233; d&#39;interop&#233;rabilit&#233; dans un flux de travail .NET Framework&#160;4
Les activités créées à l’aide de [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] ou [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] peut être utilisé dans un [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] flux de travail à l’aide de la <xref:System.Activities.Statements.Interop> activité. Cette rubrique fournit une vue d’ensemble de l’utilisation de la <xref:System.Activities.Statements.Interop> activité.  
  
> [!NOTE]
>  Le <xref:System.Activities.Statements.Interop> n’apparaît pas dans la boîte à outils du Concepteur de flux de travail, sauf si les projets du flux de travail a son **Framework cible** défini sur **.Net Framework 4** ou version ultérieure.  
  
## <a name="using-the-interop-activity-in-net-framework-45-workflows"></a>Utilisation de l'activité Interop dans les flux de travail .NET Framework 4.5  
 Cette rubrique consiste à créer une bibliothèque d'activité [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] qui contient une activité `DiscountCalculator`. Le `DiscountCalculator` calcule une remise basée sur un montant d’achat et se compose d’un <xref:System.Workflow.Activities.SequenceActivity> contenant un <xref:System.Workflow.Activities.PolicyActivity>.  
  
> [!NOTE]
>  Le [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] activité créée dans cette rubrique utilise un <xref:System.Workflow.Activities.PolicyActivity> pour implémenter la logique de l’activité. Il n’est pas requis pour utiliser les personnalisé [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] activité ou la <xref:System.Activities.Statements.Interop> activité afin d’utiliser des règles dans un [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] flux de travail. Pour obtenir un exemple d’utilisation de règles dans un [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] workflow sans utiliser le <xref:System.Activities.Statements.Interop> activité, consultez le [activité de stratégie dans le .NET Framework 4.5](../../../docs/framework/windows-workflow-foundation/samples/policy-activity-in-net-framework-4-5.md) exemple.  
  
#### <a name="to-create-the-net-framework-35-activity-library-project"></a>Pour créer le projet de bibliothèque d'activités .NET Framework 3.5  
  
1.  Ouvrez [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] et sélectionnez **New** puis **projet...** à partir de le **fichier** menu.  
  
2.  Développez le **autres Types de projets** nœud dans le **modèles installés** volet et sélectionnez **Solutions Visual Studio**.  
  
3.  Sélectionnez **Nouvelle Solution** à partir de la **Solutions Visual Studio** liste. Type de `PolicyInteropDemo` dans le **nom** puis cliquez sur **OK**.  
  
4.  Avec le bouton droit **PolicyInteropDemo** dans **l’Explorateur de solutions** et sélectionnez **Ajouter** puis **un nouveau projet...**.  
  
    > [!TIP]
    >  Si le **l’Explorateur de solutions** fenêtre n’est pas visible, sélectionnez **l’Explorateur de solutions** à partir de la **vue** menu.  
  
5.  Dans la **modèles installés** liste, sélectionnez **Visual C#** puis **Workflow**. Sélectionnez **.NET Framework 3.5** dans la liste déroulante de version du .NET Framework, puis sélectionnez **bibliothèque d’activités de flux de travail** à partir de la **modèles** liste.  
  
6.  Type de `PolicyActivityLibrary` dans le **nom** puis cliquez sur **OK**.  
  
7.  Avec le bouton droit **Activity1.cs** dans **l’Explorateur de solutions** et sélectionnez **Supprimer**. Pour confirmer, cliquez sur **OK** .  
  
#### <a name="to-create-the-discountcalculator-activity"></a>Pour créer l'activité DiscountCalculator  
  
1.  Avec le bouton droit **PolicyActivityLibrary** dans **l’Explorateur de solutions** et sélectionnez **Ajouter** puis **activité...**.  
  
2.  Sélectionnez **activité (avec séparation de code)** à partir de la **éléments Visual c#** liste. Type de `DiscountCalculator` dans le **nom** puis cliquez sur **OK**.  
  
3.  Avec le bouton droit **DiscountCalculator.xoml** dans **l’Explorateur de solutions** et sélectionnez **Afficher le Code**.  
  
4.  Ajoutez les trois propriétés suivantes à la classe `DiscountCalculator` :  
  
    ```csharp  
    public partial class DiscountCalculator : SequenceActivity  
    {  
        public double Subtotal { get; set; }  
        public double DiscountPercent { get; set; }  
        public double Total { get; set; }  
    }  
    ```  
  
5.  Avec le bouton droit **DiscountCalculator.xoml** dans **l’Explorateur de solutions** et sélectionnez **Concepteur de vues**.  
  
6.  Faites glisser un **stratégie** activité à partir de la **Windows Workflow v3.0** section de la **boîte à outils** et déposez-le dans le **DiscountCalculator** activité.  
  
    > [!TIP]
    >  Si le **boîte à outils** fenêtre n’est pas visible, sélectionnez **boîte à outils** à partir de la **vue** menu.  
  
#### <a name="to-configure-the-rules"></a>Pour configurer les règles  
  
1.  Cliquez sur récemment ajouté **stratégie** pour la sélectionner, si elle n’est pas déjà sélectionnée.  
  
2.  Cliquez sur le **RuleSetReference** propriété dans la **propriétés** fenêtre pour la sélectionner, puis cliquez sur le bouton points de suspension à droite de la propriété.  
  
    > [!TIP]
    >  Si le **propriétés** fenêtre n’est pas visible, choisissez **fenêtre Propriétés** à partir de la **vue** menu.  
  
3.  Sélectionnez **cliquer sur Nouveau**.  
  
4.  Cliquez sur **Ajouter une règle**.  
  
5.  Tapez l’expression suivante dans la **Condition** boîte.  
  
    ```  
    this.Subtotal >= 50 && this.Subtotal < 100  
    ```  
  
6.  Tapez l’expression suivante dans la **Actions Then** boîte.  
  
    ```  
    this.DiscountPercent = 0.075  
    ```  
  
7.  Cliquez sur **Ajouter une règle**.  
  
8.  Tapez l’expression suivante dans la **Condition** boîte.  
  
    ```  
    this.Subtotal >= 100  
    ```  
  
9. Tapez l’expression suivante dans la **Actions Then** boîte.  
  
    ```  
    this.DiscountPercent = 0.15  
    ```  
  
10. Cliquez sur **Ajouter une règle**.  
  
11. Tapez l’expression suivante dans la **Condition** boîte.  
  
    ```  
    this.DiscountPercent > 0  
    ```  
  
12. Tapez l’expression suivante dans la **Actions Then** boîte.  
  
    ```  
    this.Total = this.Subtotal - this.Subtotal * this.DiscountPercent  
    ```  
  
13. Tapez l’expression suivante dans la **Actions Else** boîte.  
  
    ```  
    this.Total = this.Subtotal  
    ```  
  
14. Cliquez sur **OK** pour fermer la **Éditeur d’ensemble de règles** boîte de dialogue.  
  
15. Vérifiez que le créé <xref:System.Workflow.Activities.Rules.RuleSet> est sélectionné dans le **nom** liste, puis cliquez sur **OK**.  
  
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
  
 Lorsque le <xref:System.Workflow.Activities.PolicyActivity> s’exécute, ces trois règles évaluent et modifient le `Subtotal`, `DiscountPercent`, et `Total` les valeurs de propriété de la `DiscountCalculator` activité qui permet de calculer la remise souhaitée.  
  
## <a name="using-the-discountcalculator-activity-with-the-interop-activity"></a>Utilisation de l'activité DiscountCalculator avec l'activité Interop  
 Pour utiliser le `DiscountCalculator` activité à l’intérieur un [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] flux de travail, le <xref:System.Activities.Statements.Interop> activité est utilisée. Dans cette section deux flux de travail sont créés, un à l’aide de code et l’autre à l’aide du Concepteur de flux de travail, qui montrent comment utiliser le <xref:System.Activities.Statements.Interop> activité avec le `DiscountCalculator` activité. La même application hôte est utilisée pour les deux flux de travail.  
  
#### <a name="to-create-the-host-application"></a>Pour créer l'application hôte  
  
1.  Avec le bouton droit **PolicyInteropDemo** dans **l’Explorateur de solutions** et sélectionnez **Ajouter**, puis **Nouveau projet...**.  
  
2.  Vérifiez que **.NET Framework 4.5** est sélectionné dans la liste déroulante de version .NET Framework, puis sélectionnez  **Application Console de Workflow** à partir de la **éléments Visual c#** liste.  
  
3.  Type de `PolicyInteropHost` dans le **nom** puis cliquez sur **OK**.  
  
4.  Avec le bouton droit **PolicyInteropHost** dans **l’Explorateur de solutions** et sélectionnez **propriétés**.  
  
5.  Dans la **framework cible** déroulante liste, modifiez la sélection de **.NET Framework 4 Client Profile** à **.NET Framework 4.5**. Cliquez sur **Oui** pour confirmer.  
  
6.  Avec le bouton droit **PolicyInteropHost** dans **l’Explorateur de solutions** et sélectionnez **Ajouter une référence...**.  
  
7.  Sélectionnez **PolicyActivityLibrary** à partir de la **projets** onglet, cliquez sur **OK**.  
  
8.  Avec le bouton droit **PolicyInteropHost** dans **l’Explorateur de solutions** et sélectionnez **Ajouter une référence...**.  
  
9. Sélectionnez **sous**, **System.Workflow.ComponentModel**, puis **System.workflow.ComponentModel** à partir de la **.NET** onglet, cliquez sur **OK**.  
  
10. Avec le bouton droit **PolicyInteropHost** dans **l’Explorateur de solutions** et sélectionnez **définir comme projet de démarrage**.  
  
11. Appuyez sur Ctrl+Maj+B pour générer la solution.  
  
### <a name="using-the-interop-activity-in-code"></a>Utilisation de l'activité Interop dans le code  
 Dans cet exemple, une définition de flux de travail est créée à l’aide de code qui contient le <xref:System.Activities.Statements.Interop> activité et `DiscountCalculator` activité. Ce workflow est appelé à l’aide de <xref:System.Activities.WorkflowInvoker> et les résultats de l’évaluation de la règle sont écrits dans la console à l’aide un <xref:System.Activities.Statements.WriteLine> activité.  
  
##### <a name="to-use-the-interop-activity-in-code"></a>Pour utiliser l'activité Interop dans le code  
  
1.  Avec le bouton droit **Program.cs** dans **l’Explorateur de solutions** et sélectionnez **Afficher le Code**.  
  
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
    >  Le `Subtotal`, `DiscountPercent`, et `Total` Propriétés de la `DiscountCalculator` activité sont signalées en tant qu’arguments de la <xref:System.Activities.Statements.Interop> activité et les variables de flux de travail lié à local dans le <xref:System.Activities.Statements.Interop> l’activité <xref:System.Activities.Statements.Interop.ActivityProperties%2A> collection. `Subtotal` est ajouté en tant qu’un <xref:System.Activities.ArgumentDirection> argument car le `Subtotal` flux de données vers le <xref:System.Activities.Statements.Interop> activité, et `DiscountPercent` et `Total` sont ajoutés en tant que <xref:System.Activities.ArgumentDirection> arguments parce que leurs données sont diffusées hors de la <xref:System.Activities.Statements.Interop> activité. Notez que les deux <xref:System.Activities.ArgumentDirection> arguments sont ajoutés avec les noms `DiscountPercentOut` et `TotalOut` pour indiquer qu’ils représentent <xref:System.Activities.ArgumentDirection> arguments. Le `DiscountCalculator` type est spécifié comme le <xref:System.Activities.Statements.Interop> l’activité <xref:System.Activities.Statements.Interop.ActivityType%2A>.  
  
5.  Appuyez sur Ctrl+F5 pour générer et exécuter l'application. Remplacez la valeur `Subtotal` par des valeurs différentes pour tester les différents niveaux de remise fournis par l'activité `DiscountCalculator`.  
  
    ```csharp  
    Variable<double> Subtotal = new Variable<double>  
    {  
        Default = 75.99, // Change this value.  
        Name = "Subtotal"  
    };  
    ```  
  
### <a name="using-the-interop-activity-in-the-workflow-designer"></a>Utilisation de l'activité Interop dans le Workflow Designer  
 Dans cet exemple, un flux de travail est créé à l'aide du Workflow Designer. Ce flux de travail a les mêmes fonctionnalités que l’exemple précédent, sauf qu’au lieu d’utiliser un <xref:System.Activities.Statements.WriteLine> activité pour afficher la remise, l’application hôte récupère et affiche les informations de remise lorsque le workflow est terminé. De plus, au lieu d’une utilisation des variables de flux de travail locales pour contenir les données, les arguments sont créés dans le Workflow Designer et les valeurs sont passées à partir de l’hôte lors de l’appel du flux de travail.  
  
##### <a name="to-host-the-policyactivity-using-a-workflow-designer-created-workflow"></a>Pour héberger l'activité PolicyActivity à l'aide d'un flux de travail créé par le Workflow Designer  
  
1.  Avec le bouton droit **Workflow1.xaml** dans **l’Explorateur de solutions** et sélectionnez **Supprimer**. Pour confirmer, cliquez sur **OK** .  
  
2.  Avec le bouton droit **PolicyInteropHost** dans **l’Explorateur de solutions** et sélectionnez **Ajouter**, **un nouvel élément...**.  
  
3.  Développez le **éléments Visual c#** nœud et sélectionnez **Workflow**. Sélectionnez **activité** à partir de la **éléments Visual c#** liste.  
  
4.  Type de `DiscountWorkflow` dans le **nom** puis cliquez sur **Ajouter**.  
  
5.  Cliquez sur le **Arguments** bouton sur le côté inférieur gauche du Concepteur de flux de travail pour afficher les **Arguments** volet.  
  
6.  Cliquez sur **créer un Argument**.  
  
7.  Type `Subtotal` dans le **nom** boîte, sélectionnez **dans** à partir de la **Direction** liste déroulante, sélectionnez **Double** à partir de la **type d’Argument** liste déroulante, puis appuyez sur ENTRÉE pour enregistrer l’argument.  
  
    > [!NOTE]
    >  Si **Double** ne figure pas dans le **type d’Argument** la liste déroulante, sélectionnez **Rechercher des Types...**, type `System.Double` dans le **nom du Type** puis cliquez sur **OK**.  
  
8.  Cliquez sur **créer un Argument**.  
  
9. Type `DiscountPercent` dans le **nom** boîte, sélectionnez **hors** à partir de la **Direction** liste déroulante, sélectionnez **Double** à partir de la **type d’Argument** liste déroulante, puis appuyez sur ENTRÉE pour enregistrer l’argument.  
  
10. Cliquez sur **créer un Argument**.  
  
11. Type `Total` dans le **nom** boîte, sélectionnez **hors** à partir de la **Direction** liste déroulante, sélectionnez **Double** à partir de la **type d’Argument** liste déroulante, puis appuyez sur ENTRÉE pour enregistrer l’argument.  
  
12. Cliquez sur le **Arguments** bouton sur le côté inférieur gauche du Concepteur de flux de travail pour fermer le **Arguments** volet.  
  
13. Faites glisser un **séquence** activité à partir de la **flux de contrôle** section de la **boîte à outils** et faites-le glisser jusqu'à l’aire du concepteur du flux de travail.  
  
14. Faites glisser une **Interop** activité à partir de la **Migration** section de la **boîte à outils** et déposez-le dans le **séquence** activité.  
  
15. Cliquez sur le **interopérabilité** activité sur le **cliquez sur Parcourir...** étiquette, tapez **DiscountCalculator** dans le **nom du Type** puis cliquez sur **OK**.  
  
    > [!NOTE]
    >  Lorsque le <xref:System.Activities.Statements.Interop> activité est ajoutée au flux de travail et le `DiscountCalculator` type est spécifié comme son <xref:System.Activities.Statements.Interop.ActivityType%2A>, le <xref:System.Activities.Statements.Interop> activité expose trois <xref:System.Activities.ArgumentDirection> arguments et trois <xref:System.Activities.ArgumentDirection> arguments qui représentent les trois propriétés publiques de la `DiscountCalculator` activité. Le <xref:System.Activities.ArgumentDirection> arguments ont le même nom que les trois propriétés publiques et les trois <xref:System.Activities.ArgumentDirection> arguments ont les mêmes noms avec **hors** ajouté au nom de propriété. Dans les étapes suivantes, les arguments de flux de travail créés dans les étapes précédentes sont liés à la <xref:System.Activities.Statements.Interop> arguments de l’activité.  
  
16. Type de `DiscountPercent` dans les **entrer une expression VB** située à droite de la **DiscountPercentOut** propriété et appuyez sur TAB.  
  
17. Type de `Subtotal` dans le **entrer une expression VB** située à droite de la **sous-total** propriété et appuyez sur TAB.  
  
18. Type de `Total` dans les **entrer une expression VB** située à droite de la **TotalOut** propriété et appuyez sur TAB.  
  
19. Avec le bouton droit **Program.cs** dans **l’Explorateur de solutions** et sélectionnez **Afficher le Code**.  
  
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
|RuleSet|[À l’aide de groupes de règles dans les Workflows](http://go.microsoft.com/fwlink/?LinkId=178516) et <xref:System.Workflow.Activities.Rules.RuleSet>|  
|Évaluation des règles|[Évaluation des règles dans les groupes de règles](http://go.microsoft.com/fwlink/?LinkId=178517)|  
|Chaînage des règles|[Contrôle de chaînage avant](http://go.microsoft.com/fwlink/?LinkId=178518) et [chaînage avant des règles](http://go.microsoft.com/fwlink/?LinkId=178519)|  
|Traitement des collections dans les règles|[Collections dans les règles de traitement](http://go.microsoft.com/fwlink/?LinkId=178520)|  
|Utilisation de l'activité PolicyActivity|[Utilisation de l’activité PolicyActivity](http://go.microsoft.com/fwlink/?LinkId=178521) et <xref:System.Workflow.Activities.PolicyActivity>|  
  
 Les workflows créés dans [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] n’utilisent pas toutes les fonctionnalités de règles fournies par [!INCLUDE[wf1](../../../includes/wf1-md.md)], tels que les conditions d’activité déclaratives et activités conditionnelles comme le <xref:System.Workflow.Activities.ConditionedActivityGroup> et <xref:System.Workflow.Activities.ReplicatorActivity>. Si nécessaire, ces fonctionnalités sont disponibles pour les flux de travail créés à l'aide de [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] et [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)]. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Conseils de migration](../../../docs/framework/windows-workflow-foundation//migration-guidance.md).