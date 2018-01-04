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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0a02d6dbc7c6f6583a174bd10853d8c8070ac273
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="using-the-interop-activity-in-a-net-framework-4-workflow"></a><span data-ttu-id="eef45-102">Utilisation de l'activité d'interopérabilité dans un flux de travail .NET Framework 4</span><span class="sxs-lookup"><span data-stu-id="eef45-102">Using the Interop Activity in a .NET Framework 4 Workflow</span></span>
<span data-ttu-id="eef45-103">Les activités créées à l'aide de [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] ou [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] peuvent être utilisées dans un flux de travail [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] en utilisant l'activité <xref:System.Activities.Statements.Interop>.</span><span class="sxs-lookup"><span data-stu-id="eef45-103">Activities created using [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] or [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] can be used in a [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] workflow by using the <xref:System.Activities.Statements.Interop> activity.</span></span> <span data-ttu-id="eef45-104">Cette rubrique propose une vue d'ensemble de l'utilisation de l'activité <xref:System.Activities.Statements.Interop>.</span><span class="sxs-lookup"><span data-stu-id="eef45-104">This topic provides an overview of using the <xref:System.Activities.Statements.Interop> activity.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="eef45-105">Le <xref:System.Activities.Statements.Interop> n’apparaît pas dans la boîte à outils du Concepteur de flux de travail, sauf si les projets du flux de travail a son **Framework cible** défini sur **.Net Framework 4** ou version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="eef45-105">The <xref:System.Activities.Statements.Interop> activity does not appear in the workflow designer toolbox unless the workflow's project has its **Target Framework** setting set to **.Net Framework 4** or later.</span></span>  
  
## <a name="using-the-interop-activity-in-net-framework-45-workflows"></a><span data-ttu-id="eef45-106">Utilisation de l'activité Interop dans les flux de travail .NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="eef45-106">Using the Interop Activity in .NET Framework 4.5 Workflows</span></span>  
 <span data-ttu-id="eef45-107">Cette rubrique consiste à créer une bibliothèque d'activité [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] qui contient une activité `DiscountCalculator`.</span><span class="sxs-lookup"><span data-stu-id="eef45-107">In this topic, a [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] activity library is created that contains a `DiscountCalculator` activity.</span></span> <span data-ttu-id="eef45-108">L'activité `DiscountCalculator` calcule une remise sur la base d'un montant d'achat et se compose d'un objet <xref:System.Workflow.Activities.SequenceActivity> qui contient un objet <xref:System.Workflow.Activities.PolicyActivity>.</span><span class="sxs-lookup"><span data-stu-id="eef45-108">The `DiscountCalculator` calculates a discount based on a purchase amount and consists of a <xref:System.Workflow.Activities.SequenceActivity> that contains a <xref:System.Workflow.Activities.PolicyActivity>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="eef45-109">L'activité [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] créée dans cette rubrique utilise un objet <xref:System.Workflow.Activities.PolicyActivity> pour implémenter la logique de l'activité.</span><span class="sxs-lookup"><span data-stu-id="eef45-109">The [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] activity created in this topic uses a <xref:System.Workflow.Activities.PolicyActivity> to implement the logic of the activity.</span></span> <span data-ttu-id="eef45-110">L'utilisation d'une activité [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] personnalisée ou de l'activité <xref:System.Activities.Statements.Interop> n'est pas obligatoire pour utiliser des règles dans un flux de travail [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="eef45-110">It is not required to use a custom [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] activity or the <xref:System.Activities.Statements.Interop> activity in order to use rules in a [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] workflow.</span></span> <span data-ttu-id="eef45-111">Pour obtenir un exemple d’utilisation de règles dans un [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] workflow sans utiliser le <xref:System.Activities.Statements.Interop> activité, consultez le [activité de stratégie dans le .NET Framework 4.5](../../../docs/framework/windows-workflow-foundation/samples/policy-activity-in-net-framework-4-5.md) exemple.</span><span class="sxs-lookup"><span data-stu-id="eef45-111">For an example of using rules in a [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] workflow without using the <xref:System.Activities.Statements.Interop> activity, see the [Policy Activity in .NET Framework 4.5](../../../docs/framework/windows-workflow-foundation/samples/policy-activity-in-net-framework-4-5.md) sample.</span></span>  
  
#### <a name="to-create-the-net-framework-35-activity-library-project"></a><span data-ttu-id="eef45-112">Pour créer le projet de bibliothèque d'activités .NET Framework 3.5</span><span class="sxs-lookup"><span data-stu-id="eef45-112">To create the .NET Framework 3.5 activity library project</span></span>  
  
1.  <span data-ttu-id="eef45-113">Ouvrez [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] et sélectionnez **nouveau** , puis **projet...**</span><span class="sxs-lookup"><span data-stu-id="eef45-113">Open [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] and select **New** and then **Project…**</span></span> <span data-ttu-id="eef45-114">à partir de la **fichier** menu.</span><span class="sxs-lookup"><span data-stu-id="eef45-114">from the **File** menu.</span></span>  
  
2.  <span data-ttu-id="eef45-115">Développez le **autres Types de projets** nœud dans le **modèles installés** volet et sélectionnez **Solutions Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="eef45-115">Expand the **Other Project Types** node in the **Installed Templates** pane and select **Visual Studio Solutions**.</span></span>  
  
3.  <span data-ttu-id="eef45-116">Sélectionnez **nouvelle Solution** à partir de la **Solutions Visual Studio** liste.</span><span class="sxs-lookup"><span data-stu-id="eef45-116">Select **Blank Solution** from the **Visual Studio Solutions** list.</span></span> <span data-ttu-id="eef45-117">Type `PolicyInteropDemo` dans les **nom** , puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="eef45-117">Type `PolicyInteropDemo` in the **Name** box and click **OK**.</span></span>  
  
4.  <span data-ttu-id="eef45-118">Avec le bouton droit **PolicyInteropDemo** dans **l’Explorateur de solutions** et sélectionnez **ajouter** , puis **nouveau projet...** .</span><span class="sxs-lookup"><span data-stu-id="eef45-118">Right-click **PolicyInteropDemo** in **Solution Explorer** and select **Add** and then **New Project…**.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="eef45-119">Si le **l’Explorateur de solutions** fenêtre n’est pas visible, sélectionnez **l’Explorateur de solutions** à partir de la **vue** menu.</span><span class="sxs-lookup"><span data-stu-id="eef45-119">If the **Solution Explorer** window is not visible, select **Solution Explorer** from the **View** menu.</span></span>  
  
5.  <span data-ttu-id="eef45-120">Dans le **modèles installés** liste, sélectionnez **Visual C#** , puis **Workflow**.</span><span class="sxs-lookup"><span data-stu-id="eef45-120">In the **Installed Templates** list, select **Visual C#** and then **Workflow**.</span></span> <span data-ttu-id="eef45-121">Sélectionnez **.NET Framework 3.5** dans la liste déroulante de version du .NET Framework, puis sélectionnez **bibliothèque d’activités de flux de travail** à partir de la **modèles** liste.</span><span class="sxs-lookup"><span data-stu-id="eef45-121">Select **.NET Framework 3.5** from the .NET Framework version drop-down list, and then select **Workflow Activity Library** from the **Templates** list.</span></span>  
  
6.  <span data-ttu-id="eef45-122">Type `PolicyActivityLibrary` dans les **nom** , puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="eef45-122">Type `PolicyActivityLibrary` in the **Name** box and click **OK**.</span></span>  
  
7.  <span data-ttu-id="eef45-123">Avec le bouton droit **Activity1.cs** dans **l’Explorateur de solutions** et sélectionnez **supprimer**.</span><span class="sxs-lookup"><span data-stu-id="eef45-123">Right-click **Activity1.cs** in **Solution Explorer** and select **Delete**.</span></span> <span data-ttu-id="eef45-124">Pour confirmer, cliquez sur **OK** .</span><span class="sxs-lookup"><span data-stu-id="eef45-124">Click **OK** to confirm.</span></span>  
  
#### <a name="to-create-the-discountcalculator-activity"></a><span data-ttu-id="eef45-125">Pour créer l'activité DiscountCalculator</span><span class="sxs-lookup"><span data-stu-id="eef45-125">To create the DiscountCalculator activity</span></span>  
  
1.  <span data-ttu-id="eef45-126">Avec le bouton droit **PolicyActivityLibrary** dans **l’Explorateur de solutions** et sélectionnez **ajouter** , puis **activité en cours...** .</span><span class="sxs-lookup"><span data-stu-id="eef45-126">Right-click **PolicyActivityLibrary** in **Solution Explorer** and select **Add** and then **Activity…**.</span></span>  
  
2.  <span data-ttu-id="eef45-127">Sélectionnez **activité (avec séparation de code)** à partir de la **éléments Visual c#** liste.</span><span class="sxs-lookup"><span data-stu-id="eef45-127">Select **Activity (with code separation)** from the **Visual C# Items** list.</span></span> <span data-ttu-id="eef45-128">Type `DiscountCalculator` dans les **nom** , puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="eef45-128">Type `DiscountCalculator` in the **Name** box and click **OK**.</span></span>  
  
3.  <span data-ttu-id="eef45-129">Avec le bouton droit **DiscountCalculator.xoml** dans **l’Explorateur de solutions** et sélectionnez **afficher le Code**.</span><span class="sxs-lookup"><span data-stu-id="eef45-129">Right-click **DiscountCalculator.xoml** in **Solution Explorer** and select **View Code**.</span></span>  
  
4.  <span data-ttu-id="eef45-130">Ajoutez les trois propriétés suivantes à la classe `DiscountCalculator` :</span><span class="sxs-lookup"><span data-stu-id="eef45-130">Add the following three properties to the `DiscountCalculator` class.</span></span>  
  
    ```csharp  
    public partial class DiscountCalculator : SequenceActivity  
    {  
        public double Subtotal { get; set; }  
        public double DiscountPercent { get; set; }  
        public double Total { get; set; }  
    }  
    ```  
  
5.  <span data-ttu-id="eef45-131">Avec le bouton droit **DiscountCalculator.xoml** dans **l’Explorateur de solutions** et sélectionnez **Concepteur de vue**.</span><span class="sxs-lookup"><span data-stu-id="eef45-131">Right-click **DiscountCalculator.xoml** in **Solution Explorer** and select **View Designer**.</span></span>  
  
6.  <span data-ttu-id="eef45-132">Faites glisser un **stratégie** activité à partir de la **Windows Workflow v3.0** section de la **boîte à outils** et déposez-la dans le **DiscountCalculator** activité .</span><span class="sxs-lookup"><span data-stu-id="eef45-132">Drag a **Policy** activity from the **Windows Workflow v3.0** section of the **Toolbox** and drop it in the **DiscountCalculator** activity.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="eef45-133">Si le **boîte à outils** fenêtre n’est pas visible, sélectionnez **boîte à outils** à partir de la **vue** menu.</span><span class="sxs-lookup"><span data-stu-id="eef45-133">If the **Toolbox** window is not visible, select **Toolbox** from the **View** menu.</span></span>  
  
#### <a name="to-configure-the-rules"></a><span data-ttu-id="eef45-134">Pour configurer les règles</span><span class="sxs-lookup"><span data-stu-id="eef45-134">To configure the rules</span></span>  
  
1.  <span data-ttu-id="eef45-135">Cliquez sur récemment ajouté **stratégie** activité pour la sélectionner, si elle n’est pas déjà sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="eef45-135">Click the newly added **Policy** activity to select it, if it is not already selected.</span></span>  
  
2.  <span data-ttu-id="eef45-136">Cliquez sur le **RuleSetReference** propriété dans le **propriétés** fenêtre pour la sélectionner, puis cliquez sur le bouton de sélection à droite de la propriété.</span><span class="sxs-lookup"><span data-stu-id="eef45-136">Click the **RuleSetReference** property in the **Properties** window to select it, and click the ellipsis button to the right of the property.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="eef45-137">Si le **propriétés** fenêtre n’est pas visible, choisissez **fenêtre Propriétés** à partir de la **vue** menu.</span><span class="sxs-lookup"><span data-stu-id="eef45-137">If the **Properties** window is not visible, choose **Properties Window** from the **View** menu.</span></span>  
  
3.  <span data-ttu-id="eef45-138">Sélectionnez **cliquez sur Nouveau...** .</span><span class="sxs-lookup"><span data-stu-id="eef45-138">Select **Click New…**.</span></span>  
  
4.  <span data-ttu-id="eef45-139">Cliquez sur **ajouter une règle**.</span><span class="sxs-lookup"><span data-stu-id="eef45-139">Click **Add Rule**.</span></span>  
  
5.  <span data-ttu-id="eef45-140">Tapez l’expression suivante dans le **Condition** boîte.</span><span class="sxs-lookup"><span data-stu-id="eef45-140">Type the following expression into the **Condition** box.</span></span>  
  
    ```  
    this.Subtotal >= 50 && this.Subtotal < 100  
    ```  
  
6.  <span data-ttu-id="eef45-141">Tapez l’expression suivante dans le **Actions Then** boîte.</span><span class="sxs-lookup"><span data-stu-id="eef45-141">Type the following expression into the **Then Actions** box.</span></span>  
  
    ```  
    this.DiscountPercent = 0.075  
    ```  
  
7.  <span data-ttu-id="eef45-142">Cliquez sur **ajouter une règle**.</span><span class="sxs-lookup"><span data-stu-id="eef45-142">Click **Add Rule**.</span></span>  
  
8.  <span data-ttu-id="eef45-143">Tapez l’expression suivante dans le **Condition** boîte.</span><span class="sxs-lookup"><span data-stu-id="eef45-143">Type the following expression into the **Condition** box.</span></span>  
  
    ```  
    this.Subtotal >= 100  
    ```  
  
9. <span data-ttu-id="eef45-144">Tapez l’expression suivante dans le **Actions Then** boîte.</span><span class="sxs-lookup"><span data-stu-id="eef45-144">Type the following expression into the **Then Actions** box.</span></span>  
  
    ```  
    this.DiscountPercent = 0.15  
    ```  
  
10. <span data-ttu-id="eef45-145">Cliquez sur **ajouter une règle**.</span><span class="sxs-lookup"><span data-stu-id="eef45-145">Click **Add Rule**.</span></span>  
  
11. <span data-ttu-id="eef45-146">Tapez l’expression suivante dans le **Condition** boîte.</span><span class="sxs-lookup"><span data-stu-id="eef45-146">Type the following expression into the **Condition** box.</span></span>  
  
    ```  
    this.DiscountPercent > 0  
    ```  
  
12. <span data-ttu-id="eef45-147">Tapez l’expression suivante dans le **Actions Then** boîte.</span><span class="sxs-lookup"><span data-stu-id="eef45-147">Type the following expression into the **Then Actions** box.</span></span>  
  
    ```  
    this.Total = this.Subtotal - this.Subtotal * this.DiscountPercent  
    ```  
  
13. <span data-ttu-id="eef45-148">Tapez l’expression suivante dans le **Actions Else** boîte.</span><span class="sxs-lookup"><span data-stu-id="eef45-148">Type the following expression into the **Else Actions** box.</span></span>  
  
    ```  
    this.Total = this.Subtotal  
    ```  
  
14. <span data-ttu-id="eef45-149">Cliquez sur **OK** pour fermer la **Éditeur d’ensemble de règles** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="eef45-149">Click **OK** to close the **Rule Set Editor** dialog box.</span></span>  
  
15. <span data-ttu-id="eef45-150">Vérifiez que le nouvellement créé <xref:System.Workflow.Activities.Rules.RuleSet> est sélectionné dans le **nom** liste, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="eef45-150">Ensure that the newly-created <xref:System.Workflow.Activities.Rules.RuleSet> is selected in the **Name** list, and click **OK**.</span></span>  
  
16. <span data-ttu-id="eef45-151">Appuyez sur Ctrl+Maj+B pour générer la solution.</span><span class="sxs-lookup"><span data-stu-id="eef45-151">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
 <span data-ttu-id="eef45-152">L'exemple de code suivant indique les règles ajoutées à l'activité `DiscountCalculator` lors de cette procédure.</span><span class="sxs-lookup"><span data-stu-id="eef45-152">The rules added to the `DiscountCalculator` activity in this procedure are shown in the following code example.</span></span>  
  
```  
Rule1: IF this.Subtotal >= 50 && this.Subtotal < 100   
       THEN this.DiscountPercent = 0.075   
  
Rule2: IF this. Subtotal >= 100   
       THEN this.DiscountPercent = 0.15   
  
Rule3: IF this.DiscountPercent > 0   
       THEN this.Total = this.Subtotal - this.Subtotal * this.DiscountPercent   
       ELSE this.Total = this.Subtotal  
```  
  
 <span data-ttu-id="eef45-153">Lors de l'exécution de l'objet <xref:System.Workflow.Activities.PolicyActivity>, ces trois règles évaluent et modifient les valeurs de propriété `Subtotal`, `DiscountPercent` et `Total` de l'activité `DiscountCalculator` pour calculer la remise souhaitée.</span><span class="sxs-lookup"><span data-stu-id="eef45-153">When the <xref:System.Workflow.Activities.PolicyActivity> executes, these three rules evaluate and modify the `Subtotal`, `DiscountPercent`, and `Total` property values of the `DiscountCalculator` activity to calculate the desired discount.</span></span>  
  
## <a name="using-the-discountcalculator-activity-with-the-interop-activity"></a><span data-ttu-id="eef45-154">Utilisation de l'activité DiscountCalculator avec l'activité Interop</span><span class="sxs-lookup"><span data-stu-id="eef45-154">Using the DiscountCalculator Activity with the Interop Activity</span></span>  
 <span data-ttu-id="eef45-155">Pour utiliser l'activité `DiscountCalculator` dans un flux de travail [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)], l'activité <xref:System.Activities.Statements.Interop> est utilisée.</span><span class="sxs-lookup"><span data-stu-id="eef45-155">To use the `DiscountCalculator` activity inside a [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] workflow, the <xref:System.Activities.Statements.Interop> activity is used.</span></span> <span data-ttu-id="eef45-156">Dans cette section, deux flux de travail sont créés, l'un à l'aide du code et l'autre à l'aide du Workflow Designer. Ces flux de travail indiquent comment utiliser l'activité <xref:System.Activities.Statements.Interop> avec l'activité `DiscountCalculator`.</span><span class="sxs-lookup"><span data-stu-id="eef45-156">In this section two workflows are created, one using code and one using the workflow designer, which show how to use the <xref:System.Activities.Statements.Interop> activity with the `DiscountCalculator` activity.</span></span> <span data-ttu-id="eef45-157">La même application hôte est utilisée pour les deux flux de travail.</span><span class="sxs-lookup"><span data-stu-id="eef45-157">The same host application is used for both workflows.</span></span>  
  
#### <a name="to-create-the-host-application"></a><span data-ttu-id="eef45-158">Pour créer l'application hôte</span><span class="sxs-lookup"><span data-stu-id="eef45-158">To create the host application</span></span>  
  
1.  <span data-ttu-id="eef45-159">Avec le bouton droit **PolicyInteropDemo** dans **l’Explorateur de solutions** et sélectionnez **ajouter**, puis **nouveau projet...** .</span><span class="sxs-lookup"><span data-stu-id="eef45-159">Right-click **PolicyInteropDemo** in **Solution Explorer** and select **Add**, and then **New Project…**.</span></span>  
  
2.  <span data-ttu-id="eef45-160">Vérifiez que **.NET Framework 4.5** est sélectionné dans la liste déroulante de version du .NET Framework, puis sélectionnez **Application Console de Workflow** à partir de la **éléments Visual c#** liste.</span><span class="sxs-lookup"><span data-stu-id="eef45-160">Ensure that **.NET Framework 4.5** is selected in the .NET Framework version drop-down list, and select  **Workflow Console Application** from the **Visual C# Items** list.</span></span>  
  
3.  <span data-ttu-id="eef45-161">Type `PolicyInteropHost` dans les **nom** , puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="eef45-161">Type `PolicyInteropHost` into the **Name** box and click **OK**.</span></span>  
  
4.  <span data-ttu-id="eef45-162">Avec le bouton droit **PolicyInteropHost** dans **l’Explorateur de solutions** et sélectionnez **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="eef45-162">Right-click **PolicyInteropHost** in **Solution Explorer** and select **Properties**.</span></span>  
  
5.  <span data-ttu-id="eef45-163">Dans le **framework cible** déroulante liste, modifiez la sélection à partir de **.NET Framework 4 Client Profile** à **.NET Framework 4.5**.</span><span class="sxs-lookup"><span data-stu-id="eef45-163">In the **Target framework** drop-down list, change the selection from **.NET Framework 4 Client Profile** to **.NET Framework 4.5**.</span></span> <span data-ttu-id="eef45-164">Cliquez sur **Oui** pour confirmer.</span><span class="sxs-lookup"><span data-stu-id="eef45-164">Click **Yes** to confirm.</span></span>  
  
6.  <span data-ttu-id="eef45-165">Avec le bouton droit **PolicyInteropHost** dans **l’Explorateur de solutions** et sélectionnez **ajouter une référence...** .</span><span class="sxs-lookup"><span data-stu-id="eef45-165">Right-click **PolicyInteropHost** in **Solution Explorer** and select **Add Reference…**.</span></span>  
  
7.  <span data-ttu-id="eef45-166">Sélectionnez **PolicyActivityLibrary** à partir de la **projets** onglet et cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="eef45-166">Select **PolicyActivityLibrary** from the **Projects** tab and click **OK**.</span></span>  
  
8.  <span data-ttu-id="eef45-167">Avec le bouton droit **PolicyInteropHost** dans **l’Explorateur de solutions** et sélectionnez **ajouter une référence...** .</span><span class="sxs-lookup"><span data-stu-id="eef45-167">Right-click **PolicyInteropHost** in **Solution Explorer** and select **Add Reference…**.</span></span>  
  
9. <span data-ttu-id="eef45-168">Sélectionnez **sous**, **System.Workflow.ComponentModel**, puis **System.workflow.ComponentModel** à partir de la **.NET**onglet et cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="eef45-168">Select **System.Workflow.Activities**, **System.Workflow.ComponentModel**, and then **System.Workflow.Runtime** from the **.NET** tab and click **OK**.</span></span>  
  
10. <span data-ttu-id="eef45-169">Avec le bouton droit **PolicyInteropHost** dans **l’Explorateur de solutions** et sélectionnez **définir comme projet de démarrage**.</span><span class="sxs-lookup"><span data-stu-id="eef45-169">Right-click **PolicyInteropHost** in **Solution Explorer** and select **Set as StartUp Project**.</span></span>  
  
11. <span data-ttu-id="eef45-170">Appuyez sur Ctrl+Maj+B pour générer la solution.</span><span class="sxs-lookup"><span data-stu-id="eef45-170">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
### <a name="using-the-interop-activity-in-code"></a><span data-ttu-id="eef45-171">Utilisation de l'activité Interop dans le code</span><span class="sxs-lookup"><span data-stu-id="eef45-171">Using the Interop Activity in Code</span></span>  
 <span data-ttu-id="eef45-172">Dans cet exemple, une définition de flux de travail est créée à l'aide du code qui contient les activités <xref:System.Activities.Statements.Interop> et `DiscountCalculator`.</span><span class="sxs-lookup"><span data-stu-id="eef45-172">In this example, a workflow definition is created using code that contains the <xref:System.Activities.Statements.Interop> activity and the `DiscountCalculator` activity.</span></span> <span data-ttu-id="eef45-173">Ce flux de travail est appelé à l'aide de l'objet <xref:System.Activities.WorkflowInvoker> et les résultats de l'évaluation de règle sont écrits dans la console à l'aide d'une activité <xref:System.Activities.Statements.WriteLine>.</span><span class="sxs-lookup"><span data-stu-id="eef45-173">This workflow is invoked using <xref:System.Activities.WorkflowInvoker> and the results of the rule evaluation are written to the console using a <xref:System.Activities.Statements.WriteLine> activity.</span></span>  
  
##### <a name="to-use-the-interop-activity-in-code"></a><span data-ttu-id="eef45-174">Pour utiliser l'activité Interop dans le code</span><span class="sxs-lookup"><span data-stu-id="eef45-174">To use the Interop activity in code</span></span>  
  
1.  <span data-ttu-id="eef45-175">Avec le bouton droit **Program.cs** dans **l’Explorateur de solutions** et sélectionnez **afficher le Code**.</span><span class="sxs-lookup"><span data-stu-id="eef45-175">Right-click **Program.cs** in **Solution Explorer** and select **View Code**.</span></span>  
  
2.  <span data-ttu-id="eef45-176">En tête du fichier, ajoutez l'instruction `using` suivante :</span><span class="sxs-lookup"><span data-stu-id="eef45-176">Add the following `using` statement at the top of the file.</span></span>  
  
    ```csharp  
    using PolicyActivityLibrary;  
    ```  
  
3.  <span data-ttu-id="eef45-177">Supprimez le contenu de la méthode `Main` et remplacez-le par le code suivant :</span><span class="sxs-lookup"><span data-stu-id="eef45-177">Remove the contents of the `Main` method and replace with the following code.</span></span>  
  
    ```csharp  
    static void Main(string[] args)  
    {  
        CalculateDiscountUsingCodeWorkflow();  
    }  
    ```  
  
4.  <span data-ttu-id="eef45-178">Dans la classe `Program`, créez une méthode appelée `CalculateDiscountUsingCodeWorkflow` qui contient le code suivant :</span><span class="sxs-lookup"><span data-stu-id="eef45-178">Create a new method in the `Program` class called `CalculateDiscountUsingCodeWorkflow` that contains the following code.</span></span>  
  
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
    >  <span data-ttu-id="eef45-179">Les propriétés `Subtotal`, `DiscountPercent` et `Total` de l'activité `DiscountCalculator` sont signalées en tant qu'arguments de l'activité <xref:System.Activities.Statements.Interop> et liées à des variables de flux de travail locales dans la collection <xref:System.Activities.Statements.Interop> de l'activité <xref:System.Activities.Statements.Interop.ActivityProperties%2A>.</span><span class="sxs-lookup"><span data-stu-id="eef45-179">The `Subtotal`, `DiscountPercent`, and `Total` properties of the `DiscountCalculator` activity are surfaced as arguments of the <xref:System.Activities.Statements.Interop> activity, and bound to local workflow variables in the <xref:System.Activities.Statements.Interop> activity’s <xref:System.Activities.Statements.Interop.ActivityProperties%2A> collection.</span></span> <span data-ttu-id="eef45-180">`Subtotal` est ajouté en tant qu'argument <xref:System.Activities.ArgumentDirection.In>, car les données `Subtotal` sont diffusées dans l'activité <xref:System.Activities.Statements.Interop>, et `DiscountPercent` et `Total` sont ajoutés comme arguments <xref:System.Activities.ArgumentDirection.Out>, car leurs données sont diffusées hors de l'activité <xref:System.Activities.Statements.Interop>.</span><span class="sxs-lookup"><span data-stu-id="eef45-180">`Subtotal` is added as an <xref:System.Activities.ArgumentDirection.In> argument because the `Subtotal` data flows into the <xref:System.Activities.Statements.Interop> activity, and `DiscountPercent` and `Total` are added as <xref:System.Activities.ArgumentDirection.Out> arguments because their data flows out of the <xref:System.Activities.Statements.Interop> activity.</span></span> <span data-ttu-id="eef45-181">Notez que les deux arguments <xref:System.Activities.ArgumentDirection.Out> sont ajoutés avec les noms `DiscountPercentOut` et `TotalOut` pour indiquer qu'ils représentent des arguments <xref:System.Activities.ArgumentDirection.Out>.</span><span class="sxs-lookup"><span data-stu-id="eef45-181">Note that the two <xref:System.Activities.ArgumentDirection.Out> arguments are added with the names `DiscountPercentOut` and `TotalOut` to indicate that they represent <xref:System.Activities.ArgumentDirection.Out> arguments.</span></span> <span data-ttu-id="eef45-182">Le type `DiscountCalculator` est spécifié comme l'objet <xref:System.Activities.Statements.Interop> de l'activité <xref:System.Activities.Statements.Interop.ActivityType%2A>.</span><span class="sxs-lookup"><span data-stu-id="eef45-182">The `DiscountCalculator` type is specified as the <xref:System.Activities.Statements.Interop> activity’s <xref:System.Activities.Statements.Interop.ActivityType%2A>.</span></span>  
  
5.  <span data-ttu-id="eef45-183">Appuyez sur Ctrl+F5 pour générer et exécuter l'application.</span><span class="sxs-lookup"><span data-stu-id="eef45-183">Press CTRL+F5 to build and run the application.</span></span> <span data-ttu-id="eef45-184">Remplacez la valeur `Subtotal` par des valeurs différentes pour tester les différents niveaux de remise fournis par l'activité `DiscountCalculator`.</span><span class="sxs-lookup"><span data-stu-id="eef45-184">Substitute different values for the `Subtotal` value to test out the different discount levels provided by the `DiscountCalculator` activity.</span></span>  
  
    ```csharp  
    Variable<double> Subtotal = new Variable<double>  
    {  
        Default = 75.99, // Change this value.  
        Name = "Subtotal"  
    };  
    ```  
  
### <a name="using-the-interop-activity-in-the-workflow-designer"></a><span data-ttu-id="eef45-185">Utilisation de l'activité Interop dans le Workflow Designer</span><span class="sxs-lookup"><span data-stu-id="eef45-185">Using the Interop Activity in the Workflow Designer</span></span>  
 <span data-ttu-id="eef45-186">Dans cet exemple, un flux de travail est créé à l'aide du Workflow Designer.</span><span class="sxs-lookup"><span data-stu-id="eef45-186">In this example, a workflow is created using the workflow designer.</span></span> <span data-ttu-id="eef45-187">Ce flux de travail a les mêmes fonctionnalités que l'exemple précédent, sauf qu'au lieu d'utiliser une activité <xref:System.Activities.Statements.WriteLine> pour afficher la remise, l'application hôte récupère et affiche les informations de remise à la fin du flux de travail.</span><span class="sxs-lookup"><span data-stu-id="eef45-187">This workflow has the same functionality as the previous example, except than instead of using a <xref:System.Activities.Statements.WriteLine> activity to display the discount, the host application retrieves and displays the discount information when the workflow completes.</span></span> <span data-ttu-id="eef45-188">De plus, au lieu d'une utilisation des variables de flux de travail locales pour contenir les données, les arguments sont créés dans le Workflow Designer et les valeurs sont passées à partir de l'hôte lors de l'appel du flux de travail.</span><span class="sxs-lookup"><span data-stu-id="eef45-188">Also, instead of using local workflow variables to contain the data, arguments are created in the workflow designer and the values are passed in from the host when the workflow is invoked.</span></span>  
  
##### <a name="to-host-the-policyactivity-using-a-workflow-designer-created-workflow"></a><span data-ttu-id="eef45-189">Pour héberger l'activité PolicyActivity à l'aide d'un flux de travail créé par le Workflow Designer</span><span class="sxs-lookup"><span data-stu-id="eef45-189">To host the PolicyActivity using a Workflow Designer-created workflow</span></span>  
  
1.  <span data-ttu-id="eef45-190">Avec le bouton droit **Workflow1.xaml** dans **l’Explorateur de solutions** et sélectionnez **supprimer**.</span><span class="sxs-lookup"><span data-stu-id="eef45-190">Right-click **Workflow1.xaml** in **Solution Explorer** and select **Delete**.</span></span> <span data-ttu-id="eef45-191">Pour confirmer, cliquez sur **OK** .</span><span class="sxs-lookup"><span data-stu-id="eef45-191">Click **OK** to confirm.</span></span>  
  
2.  <span data-ttu-id="eef45-192">Avec le bouton droit **PolicyInteropHost** dans **l’Explorateur de solutions** et sélectionnez **ajouter**, **un nouvel élément...** .</span><span class="sxs-lookup"><span data-stu-id="eef45-192">Right-click **PolicyInteropHost** in **Solution Explorer** and select **Add**, **New Item…**.</span></span>  
  
3.  <span data-ttu-id="eef45-193">Développez le **éléments Visual c#** nœud et sélectionnez **Workflow**.</span><span class="sxs-lookup"><span data-stu-id="eef45-193">Expand the **Visual C# Items** node and select **Workflow**.</span></span> <span data-ttu-id="eef45-194">Sélectionnez **activité** à partir de la **éléments Visual c#** liste.</span><span class="sxs-lookup"><span data-stu-id="eef45-194">Select **Activity** from the **Visual C# Items** list.</span></span>  
  
4.  <span data-ttu-id="eef45-195">Type `DiscountWorkflow` dans les **nom** , puis cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="eef45-195">Type `DiscountWorkflow` into the **Name** box and click **Add**.</span></span>  
  
5.  <span data-ttu-id="eef45-196">Cliquez sur le **Arguments** bouton sur le côté inférieur gauche du Concepteur de flux de travail pour afficher la **Arguments** volet.</span><span class="sxs-lookup"><span data-stu-id="eef45-196">Click the **Arguments** button on the lower left side of the workflow designer to display the **Arguments** pane.</span></span>  
  
6.  <span data-ttu-id="eef45-197">Cliquez sur **créer un Argument**.</span><span class="sxs-lookup"><span data-stu-id="eef45-197">Click **Create Argument**.</span></span>  
  
7.  <span data-ttu-id="eef45-198">Type `Subtotal` dans les **nom** boîte, sélectionnez **dans** à partir de la **Direction** liste déroulante, sélectionnez **Double** à partir de la **Type d’argument** liste déroulante, puis appuyez sur ENTRÉE pour enregistrer l’argument.</span><span class="sxs-lookup"><span data-stu-id="eef45-198">Type `Subtotal` into the **Name** box, select **In** from the **Direction** drop-down, select **Double** from the **Argument type** drop-down, and then press ENTER to save the argument.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="eef45-199">Si **Double** ne figure pas dans le **type d’Argument** la liste déroulante, sélectionnez **rechercher des Types...** , type `System.Double` dans les **nom de Type** , puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="eef45-199">If **Double** is not in the **Argument type** drop-down list, select **Browse for Types …**, type `System.Double` in the **Type Name** box, and click **OK**.</span></span>  
  
8.  <span data-ttu-id="eef45-200">Cliquez sur **créer un Argument**.</span><span class="sxs-lookup"><span data-stu-id="eef45-200">Click **Create Argument**.</span></span>  
  
9. <span data-ttu-id="eef45-201">Type `DiscountPercent` dans les **nom** boîte, sélectionnez **hors** à partir de la **Direction** liste déroulante, sélectionnez **Double** à partir de la **Type d’argument** liste déroulante, puis appuyez sur ENTRÉE pour enregistrer l’argument.</span><span class="sxs-lookup"><span data-stu-id="eef45-201">Type `DiscountPercent` into the **Name** box, select **Out** from the **Direction** drop-down, select **Double** from the **Argument type** drop-down, and then press ENTER to save the argument.</span></span>  
  
10. <span data-ttu-id="eef45-202">Cliquez sur **créer un Argument**.</span><span class="sxs-lookup"><span data-stu-id="eef45-202">Click **Create Argument**.</span></span>  
  
11. <span data-ttu-id="eef45-203">Type `Total` dans les **nom** boîte, sélectionnez **hors** à partir de la **Direction** liste déroulante, sélectionnez **Double** à partir de la **Type d’argument** liste déroulante, puis appuyez sur ENTRÉE pour enregistrer l’argument.</span><span class="sxs-lookup"><span data-stu-id="eef45-203">Type `Total` into the **Name** box, select **Out** from the **Direction** drop-down, select **Double** from the **Argument type** drop-down, and then press ENTER to save the argument.</span></span>  
  
12. <span data-ttu-id="eef45-204">Cliquez sur le **Arguments** bouton sur le côté inférieur gauche du Concepteur de flux de travail pour fermer la **Arguments** volet.</span><span class="sxs-lookup"><span data-stu-id="eef45-204">Click the **Arguments** button on the lower left side of the workflow designer to close the **Arguments** pane.</span></span>  
  
13. <span data-ttu-id="eef45-205">Faites glisser un **séquence** activité à partir de la **flux de contrôle** section de la **boîte à outils** et déposez-le sur l’aire de conception de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="eef45-205">Drag a **Sequence** activity from the **Control Flow** section of the **Toolbox** and drop it onto the workflow designer surface.</span></span>  
  
14. <span data-ttu-id="eef45-206">Faites glisser un **Interop** activité à partir de la **Migration** section de la **boîte à outils** et déposez-la dans le **séquence** activité.</span><span class="sxs-lookup"><span data-stu-id="eef45-206">Drag an **Interop** activity from the **Migration** section of the **Toolbox** and drop it in the **Sequence** activity.</span></span>  
  
15. <span data-ttu-id="eef45-207">Cliquez sur le **Interop** activité sur le **cliquez pour parcourir...**</span><span class="sxs-lookup"><span data-stu-id="eef45-207">Click the **Interop** activity on the **Click to browse…**</span></span> <span data-ttu-id="eef45-208">étiquette, tapez **DiscountCalculator** dans les **nom de Type** , puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="eef45-208">label, type **DiscountCalculator** in the **Type Name** box, and click **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="eef45-209">Lorsque l'activité <xref:System.Activities.Statements.Interop> est ajoutée au flux de travail et que le type `DiscountCalculator` est spécifié comme sa propriété <xref:System.Activities.Statements.Interop.ActivityType%2A>, l'activité <xref:System.Activities.Statements.Interop> expose trois arguments <xref:System.Activities.ArgumentDirection.In> et trois arguments <xref:System.Activities.ArgumentDirection.Out> qui représentent les trois propriétés publiques de l'activité `DiscountCalculator`.</span><span class="sxs-lookup"><span data-stu-id="eef45-209">When the <xref:System.Activities.Statements.Interop> activity is added to the workflow and the `DiscountCalculator` type is specified as its <xref:System.Activities.Statements.Interop.ActivityType%2A>, the <xref:System.Activities.Statements.Interop> activity exposes three <xref:System.Activities.ArgumentDirection.In> arguments and three <xref:System.Activities.ArgumentDirection.Out> arguments that represent the three public properties of the `DiscountCalculator` activity.</span></span> <span data-ttu-id="eef45-210">Le <xref:System.Activities.ArgumentDirection.In> arguments ont le même nom que les trois propriétés publiques et les trois <xref:System.Activities.ArgumentDirection.Out> arguments ont les mêmes noms avec **hors** ajouté au nom de propriété.</span><span class="sxs-lookup"><span data-stu-id="eef45-210">The <xref:System.Activities.ArgumentDirection.In> arguments have the same name as the three public properties, and the three <xref:System.Activities.ArgumentDirection.Out> arguments have the same names with **Out** appended to the property name.</span></span> <span data-ttu-id="eef45-211">Dans les étapes suivantes, les arguments de flux de travail créés dans les étapes précédentes sont liés aux arguments de l'activité <xref:System.Activities.Statements.Interop>.</span><span class="sxs-lookup"><span data-stu-id="eef45-211">In the following steps, the workflow arguments created in the previous steps are bound to the <xref:System.Activities.Statements.Interop> activity’s arguments.</span></span>  
  
16. <span data-ttu-id="eef45-212">Type `DiscountPercent` dans les **entrer une expression VB** zone située à droite de la **DiscountPercentOut** propriété et appuyez sur TAB.</span><span class="sxs-lookup"><span data-stu-id="eef45-212">Type `DiscountPercent` into the **Enter a VB expression** box to the right of the **DiscountPercentOut** property and press TAB.</span></span>  
  
17. <span data-ttu-id="eef45-213">Type `Subtotal` dans les **entrer une expression VB** zone située à droite de la **sous-total** propriété et appuyez sur TAB.</span><span class="sxs-lookup"><span data-stu-id="eef45-213">Type `Subtotal` into the **Enter a VB expression** box to the right of the **Subtotal** property and press TAB.</span></span>  
  
18. <span data-ttu-id="eef45-214">Type `Total` dans les **entrer une expression VB** zone située à droite de la **TotalOut** propriété et appuyez sur TAB.</span><span class="sxs-lookup"><span data-stu-id="eef45-214">Type `Total` into the **Enter a VB expression** box to the right of the **TotalOut** property and press TAB.</span></span>  
  
19. <span data-ttu-id="eef45-215">Avec le bouton droit **Program.cs** dans **l’Explorateur de solutions** et sélectionnez **afficher le Code**.</span><span class="sxs-lookup"><span data-stu-id="eef45-215">Right-click **Program.cs** in **Solution Explorer** and select **View Code**.</span></span>  
  
20. <span data-ttu-id="eef45-216">En tête du fichier, ajoutez l'instruction `using` suivante :</span><span class="sxs-lookup"><span data-stu-id="eef45-216">Add the following `using` statement at the top of the file.</span></span>  
  
    ```csharp  
    using System.Collections.Generic;  
    ```  
  
21. <span data-ttu-id="eef45-217">Supprimez l'appel à la méthode `CalculateDiscountInCode` dans la méthode `Main` et ajoutez le code suivant :</span><span class="sxs-lookup"><span data-stu-id="eef45-217">Comment out the call to the `CalculateDiscountInCode` method in the `Main` method and add the following code.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="eef45-218">Si vous n'avez pas suivi la procédure précédente et si le code `Main` par défaut est présent, remplacez le contenu de `Main` par le code suivant :</span><span class="sxs-lookup"><span data-stu-id="eef45-218">If you did not follow the previous procedure and the default `Main` code is present, replace the contents of `Main` with the following code.</span></span>  
  
    ```csharp  
    static void Main(string[] args)  
    {  
        CalculateDiscountUsingDesignerWorkflow();  
        //CalculateDiscountUsingCodeWorkflow();  
    }  
    ```  
  
22. <span data-ttu-id="eef45-219">Dans la classe `Program`, créez une méthode appelée `CalculateDiscountUsingDesignerWorkflow` qui contient le code suivant :</span><span class="sxs-lookup"><span data-stu-id="eef45-219">Create a new method in the `Program` class called `CalculateDiscountUsingDesignerWorkflow` that contains the following code.</span></span>  
  
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
  
23. <span data-ttu-id="eef45-220">Appuyez sur Ctrl+F5 pour générer et exécuter l'application.</span><span class="sxs-lookup"><span data-stu-id="eef45-220">Press CTRL+F5 to build and run the application.</span></span> <span data-ttu-id="eef45-221">Pour spécifier un montant `Subtotal` différent, modifiez la valeur de `SubtotalValue` dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="eef45-221">To specify a different `Subtotal` amount, change the value of `SubtotalValue` in the following code.</span></span>  
  
    ```csharp  
    double SubtotalValue = 125.99; // Change this value.  
    ```  
  
## <a name="rules-features-overview"></a><span data-ttu-id="eef45-222">Vue d'ensemble des fonctionnalités des règles</span><span class="sxs-lookup"><span data-stu-id="eef45-222">Rules Features Overview</span></span>  
 <span data-ttu-id="eef45-223">Le moteur de règles [!INCLUDE[wf1](../../../includes/wf1-md.md)] fournit un support pour le traitement des règles dans l'ordre de priorité à l'aide du chaînage avant.</span><span class="sxs-lookup"><span data-stu-id="eef45-223">The [!INCLUDE[wf1](../../../includes/wf1-md.md)] rules engine provides support for processing rules in a priority-based manner with support for forward chaining.</span></span> <span data-ttu-id="eef45-224">Les règles peuvent être évaluées pour un seul élément ou pour les éléments d'une collection.</span><span class="sxs-lookup"><span data-stu-id="eef45-224">Rules can be evaluated for a single item or for items in a collection.</span></span> <span data-ttu-id="eef45-225">Pour obtenir une vue d'ensemble des règles, ainsi que des informations sur des fonctionnalités particulières des règles, veuillez vous reporter au tableau suivant :</span><span class="sxs-lookup"><span data-stu-id="eef45-225">For an overview of rules and information on specific rules functionality, please refer to the following table.</span></span>  
  
|<span data-ttu-id="eef45-226">Fonctionnalité des règles</span><span class="sxs-lookup"><span data-stu-id="eef45-226">Rules Feature</span></span>|<span data-ttu-id="eef45-227">Documentation</span><span class="sxs-lookup"><span data-stu-id="eef45-227">Documentation</span></span>|  
|-------------------|-------------------|  
|<span data-ttu-id="eef45-228">Vue d'ensemble des règles</span><span class="sxs-lookup"><span data-stu-id="eef45-228">Rules Overview</span></span>|[<span data-ttu-id="eef45-229">Présentation du moteur de règles Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="eef45-229">Introduction to the Windows Workflow Foundation Rules Engine</span></span>](http://go.microsoft.com/fwlink/?LinkID=152836)|  
|<span data-ttu-id="eef45-230">RuleSet</span><span class="sxs-lookup"><span data-stu-id="eef45-230">RuleSet</span></span>|<span data-ttu-id="eef45-231">[À l’aide de groupes de règles dans les Workflows](http://go.microsoft.com/fwlink/?LinkId=178516) et<xref:System.Workflow.Activities.Rules.RuleSet></span><span class="sxs-lookup"><span data-stu-id="eef45-231">[Using RuleSets in Workflows](http://go.microsoft.com/fwlink/?LinkId=178516) and <xref:System.Workflow.Activities.Rules.RuleSet></span></span>|  
|<span data-ttu-id="eef45-232">Évaluation des règles</span><span class="sxs-lookup"><span data-stu-id="eef45-232">Evaluation of Rules</span></span>|[<span data-ttu-id="eef45-233">Évaluation des règles dans les ensembles de règles</span><span class="sxs-lookup"><span data-stu-id="eef45-233">Rules Evaluation in RuleSets</span></span>](http://go.microsoft.com/fwlink/?LinkId=178517)|  
|<span data-ttu-id="eef45-234">Chaînage des règles</span><span class="sxs-lookup"><span data-stu-id="eef45-234">Rules Chaining</span></span>|<span data-ttu-id="eef45-235">[Contrôle de chaînage avant](http://go.microsoft.com/fwlink/?LinkId=178518) et [chaînage avant des règles](http://go.microsoft.com/fwlink/?LinkId=178519)</span><span class="sxs-lookup"><span data-stu-id="eef45-235">[Forward Chaining Control](http://go.microsoft.com/fwlink/?LinkId=178518) and [Forward Chaining of Rules](http://go.microsoft.com/fwlink/?LinkId=178519)</span></span>|  
|<span data-ttu-id="eef45-236">Traitement des collections dans les règles</span><span class="sxs-lookup"><span data-stu-id="eef45-236">Processing Collections in Rules</span></span>|[<span data-ttu-id="eef45-237">Collections dans les règles de traitement</span><span class="sxs-lookup"><span data-stu-id="eef45-237">Processing Collections in Rules</span></span>](http://go.microsoft.com/fwlink/?LinkId=178520)|  
|<span data-ttu-id="eef45-238">Utilisation de l'activité PolicyActivity</span><span class="sxs-lookup"><span data-stu-id="eef45-238">Using the PolicyActivity</span></span>|<span data-ttu-id="eef45-239">[À l’aide de l’activité PolicyActivity](http://go.microsoft.com/fwlink/?LinkId=178521) et<xref:System.Workflow.Activities.PolicyActivity></span><span class="sxs-lookup"><span data-stu-id="eef45-239">[Using the PolicyActivity Activity](http://go.microsoft.com/fwlink/?LinkId=178521) and <xref:System.Workflow.Activities.PolicyActivity></span></span>|  
  
 <span data-ttu-id="eef45-240">Les flux de travail créés dans [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] n'utilisent pas toutes les fonctionnalités de règles fournies par [!INCLUDE[wf1](../../../includes/wf1-md.md)], telles que les conditions d'activité déclaratives et les activités conditionnelles comme <xref:System.Workflow.Activities.ConditionedActivityGroup> et <xref:System.Workflow.Activities.ReplicatorActivity>.</span><span class="sxs-lookup"><span data-stu-id="eef45-240">Workflows created in [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] do not use all of the rules features provided by [!INCLUDE[wf1](../../../includes/wf1-md.md)], such as declarative activity conditions and conditional activities such as the <xref:System.Workflow.Activities.ConditionedActivityGroup> and <xref:System.Workflow.Activities.ReplicatorActivity>.</span></span> <span data-ttu-id="eef45-241">Si nécessaire, ces fonctionnalités sont disponibles pour les flux de travail créés à l'aide de [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] et [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="eef45-241">If required, this functionality is available for workflows created using [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] and [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)].</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="eef45-242">[Conseils de migration](../../../docs/framework/windows-workflow-foundation/migration-guidance.md).</span><span class="sxs-lookup"><span data-stu-id="eef45-242"> [Migration Guidance](../../../docs/framework/windows-workflow-foundation/migration-guidance.md).</span></span>
