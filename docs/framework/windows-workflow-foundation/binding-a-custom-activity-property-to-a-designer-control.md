---
title: "Liaison d’une propriété d’activité personnalisée à un contrôle de concepteur"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2e8061ea-10f5-407c-a31f-d0d74ce12f27
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 79ceeb7406fdae9b4044053e12bec2aad926f26e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="binding-a-custom-activity-property-to-a-designer-control"></a><span data-ttu-id="ea6b7-102">Liaison d’une propriété d’activité personnalisée à un contrôle de concepteur</span><span class="sxs-lookup"><span data-stu-id="ea6b7-102">Binding a custom activity property to a designer control</span></span>
<span data-ttu-id="ea6b7-103">La liaison contrôle de concepteur de zone de texte à un argument d’activité est assez simple . Toutefois, la liaison d’un contrôle de concepteur complexe (tel qu’une zone de liste déroulante) à un argument d’activité peut poser des problèmes.</span><span class="sxs-lookup"><span data-stu-id="ea6b7-103">Binding a text box designer control to an activity argument is fairly straightforward; binding a complex designer control (such as a combo box) to an activity argument may present challenges, however.</span></span> <span data-ttu-id="ea6b7-104">Cette rubrique explique comment lier un argument d'activité à un contrôle de zone de liste déroulante sur un concepteur d'activités personnalisées.</span><span class="sxs-lookup"><span data-stu-id="ea6b7-104">This topic discusses how to bind an activity argument to a combo box control on a custom activity designer.</span></span>  
  
#### <a name="creating-the-combo-box-item-converter"></a><span data-ttu-id="ea6b7-105">Création du convertisseur d'éléments de zone de liste déroulante</span><span class="sxs-lookup"><span data-stu-id="ea6b7-105">Creating the combo box item converter</span></span>  
  
1.  <span data-ttu-id="ea6b7-106">Créez une solution vide appelée CustomProperty dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ea6b7-106">Create a new empty solution in Visual Studio called CustomProperty.</span></span>  
  
2.  <span data-ttu-id="ea6b7-107">Créez une classe appelée ComboBoxItemConverter.</span><span class="sxs-lookup"><span data-stu-id="ea6b7-107">Create a new class called ComboBoxItemConverter.</span></span> <span data-ttu-id="ea6b7-108">Ajoutez une référence à System.Windows.Data et faites dériver la classe de <xref:System.Windows.Data.IValueConverter>.</span><span class="sxs-lookup"><span data-stu-id="ea6b7-108">Add a reference to System.Windows.Data, and have the class derive from <xref:System.Windows.Data.IValueConverter>.</span></span> <span data-ttu-id="ea6b7-109">Faites en sorte que Visual Studio implémente l'interface pour générer des stubs pour `Convert` et `ConvertBack`.</span><span class="sxs-lookup"><span data-stu-id="ea6b7-109">Have Visual Studio implement the interface to generate stubs for `Convert` and `ConvertBack`.</span></span>  
  
3.  <span data-ttu-id="ea6b7-110">Ajoutez le code suivant à la méthode `Convert`.</span><span class="sxs-lookup"><span data-stu-id="ea6b7-110">Add the following code to the `Convert` method.</span></span> <span data-ttu-id="ea6b7-111">Ce code convertit l'<xref:System.Activities.InArgument%601> de l'activité de type <xref:System.String> en la valeur à placer dans le concepteur.</span><span class="sxs-lookup"><span data-stu-id="ea6b7-111">This code converts the activity's <xref:System.Activities.InArgument%601> of type <xref:System.String> to the value to be placed in the designer.</span></span>  
  
    ```  
    ModelItem modelItem = value as ModelItem;  
    if (value != null)  
    {  
        InArgument<string> inArgument = modelItem.GetCurrentValue() as InArgument<string>;  
  
        if (inArgument != null)  
        {  
            Activity<string> expression = inArgument.Expression;  
            VisualBasicValue<string> vbexpression = expression as VisualBasicValue<string>;  
            Literal<string> literal = expression as Literal<string>;  
  
            if (literal != null)  
            {  
                return "\"" + literal.Value + "\"";  
            }  
            else if (vbexpression != null)  
            {  
                return vbexpression.ExpressionText;  
            }  
        }  
    }  
    return null;  
    ```  
  
     <span data-ttu-id="ea6b7-112">L'expression dans l'extrait de code ci-dessus peut également être créée à l'aide de <xref:Microsoft.CSharp.Activities.CSharpValue%601> à la place de <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601>.</span><span class="sxs-lookup"><span data-stu-id="ea6b7-112">The expression in the above code snippet can also be created using <xref:Microsoft.CSharp.Activities.CSharpValue%601> instead of <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601>.</span></span>  
  
    ```  
    ModelItem modelItem = value as ModelItem;  
    if (value != null)  
    {  
        InArgument<string> inArgument = modelItem.GetCurrentValue() as InArgument<string>;  
  
        if (inArgument != null)  
        {  
            Activity<string> expression = inArgument.Expression;  
            CSharpValue<string> csexpression = expression as CSharpValue<string>;  
            Literal<string> literal = expression as Literal<string>;  
  
            if (literal != null)  
            {  
                return "\"" + literal.Value + "\"";  
            }  
            else if (csexpression != null)  
            {  
                return csexpression.ExpressionText;  
            }  
        }  
    }  
    return null;  
    ```  
  
4.  <span data-ttu-id="ea6b7-113">Ajoutez le code suivant à la méthode `ConvertBack`.</span><span class="sxs-lookup"><span data-stu-id="ea6b7-113">Add the following code to the `ConvertBack` method.</span></span> <span data-ttu-id="ea6b7-114">Ce code convertit à nouveau l'élément de zone de liste déroulante entrant en <xref:System.Activities.InArgument%601>.</span><span class="sxs-lookup"><span data-stu-id="ea6b7-114">This code converts the incoming combo box item back to an <xref:System.Activities.InArgument%601>.</span></span>  
  
    ```  
    // Convert combo box value to InArgument<string>  
                string itemContent = (string)((ComboBoxItem)value).Content;  
                VisualBasicValue<string> vbArgument = new VisualBasicValue<string>(itemContent);  
                InArgument<string> inArgument = new InArgument<string>(vbArgument);  
                return inArgument;  
    ```  
  
     <span data-ttu-id="ea6b7-115">L'expression dans l'extrait de code ci-dessus peut également être créée à l'aide de <xref:Microsoft.CSharp.Activities.CSharpValue%601> à la place de <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601>.</span><span class="sxs-lookup"><span data-stu-id="ea6b7-115">The expression in the above code snippet can also be created using <xref:Microsoft.CSharp.Activities.CSharpValue%601> instead of <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601>.</span></span>  
  
    ```  
    // Convert combo box value to InArgument<string>  
                string itemContent = (string)((ComboBoxItem)value).Content;  
                CSharpValue<string> csArgument = new CSharpValue<string>(itemContent);  
                InArgument<string> inArgument = new InArgument<string>(csArgument);  
                return inArgument;  
    ```  
  
#### <a name="adding-the-comboboxitemconverter-to-the-custom-designer-of-an-activity"></a><span data-ttu-id="ea6b7-116">Ajout de ComboBoxItemConverter au concepteur personnalisé d'une activité</span><span class="sxs-lookup"><span data-stu-id="ea6b7-116">Adding the ComboBoxItemConverter to the custom designer of an activity</span></span>  
  
1.  <span data-ttu-id="ea6b7-117">Ajoutez un nouvel élément au projet.</span><span class="sxs-lookup"><span data-stu-id="ea6b7-117">Add a new item to the project.</span></span> <span data-ttu-id="ea6b7-118">Dans la boîte de dialogue Nouvel élément, sélectionnez le nœud de workflow et ActivityDesigner comme type de nouvel élément.</span><span class="sxs-lookup"><span data-stu-id="ea6b7-118">In the New Item dialog, select the Workflow node and select Activity Designer as the type of the new item.</span></span> <span data-ttu-id="ea6b7-119">Nommez le CustomPropertyDesigner de l'élément.</span><span class="sxs-lookup"><span data-stu-id="ea6b7-119">Name the item CustomPropertyDesigner.</span></span>  
  
2.  <span data-ttu-id="ea6b7-120">Ajoutez une zone de liste déroulante au nouveau concepteur.</span><span class="sxs-lookup"><span data-stu-id="ea6b7-120">Add a Combo Box to the new designer.</span></span> <span data-ttu-id="ea6b7-121">Dans la propriété Items, ajoutez plusieurs éléments à la zone de liste déroulante, avec les valeurs de contenu « Item1 » et « Item2 ».</span><span class="sxs-lookup"><span data-stu-id="ea6b7-121">In the Items property, add a couple of items to the combo box, with Content values of "Item1" and 'Item2".</span></span>  
  
3.  <span data-ttu-id="ea6b7-122">Modifiez le code XAML de la zone de liste déroulante pour ajouter le nouveau convertisseur d'éléments comme convertisseur à utiliser pour la zone de liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="ea6b7-122">Modify the XAML of the combo box to add the new item converter as the item converter to be used for the combo box.</span></span> <span data-ttu-id="ea6b7-123">Le convertisseur est ajouté comme ressource dans le segment ActivityDesigner.Resources et spécifie le convertisseur dans l'attribut Converter pour la <xref:System.Windows.Controls.ComboBox>.</span><span class="sxs-lookup"><span data-stu-id="ea6b7-123">The converter is added as a resource in the ActivityDesigner.Resources segment, and specifies the converter in the Converter attribute for the <xref:System.Windows.Controls.ComboBox>.</span></span> <span data-ttu-id="ea6b7-124">Notez que l'espace de noms du projet est spécifié dans les attributs Namespaces pour le concepteur d'activité ; si le concepteur doit être utilisé dans un projet différent, cet espace de noms devra être modifié.</span><span class="sxs-lookup"><span data-stu-id="ea6b7-124">Note that the namespace of the project is specified in the namespaces attributes for the activity designer; if the designer is to be used in a different project, this namespace will need to be changed.</span></span>  
  
    ```  
    <sap:ActivityDesigner x:Class="CustomProperty.CustomPropertyDesigner"  
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
        xmlns:c="clr-namespace:CustomProperty"  
        xmlns:sap="clr-namespace:System.Activities.Presentation;assembly=System.Activities.Presentation"  
        xmlns:sapv="clr-namespace:System.Activities.Presentation.View;assembly=System.Activities.Presentation">  
  
        <sap:ActivityDesigner.Resources>  
            <ResourceDictionary>  
                <c:ComboBoxItemConverter x:Key="comboBoxItemConverter"/>  
            </ResourceDictionary>  
        </sap:ActivityDesigner.Resources>  
        <Grid>  
            <ComboBox SelectedValue="{Binding Path=ModelItem.Text, Mode=TwoWay, Converter={StaticResource comboBoxItemConverter}}"  Height="23" HorizontalAlignment="Left" Margin="132,5,0,0" Name="comboBox1" VerticalAlignment="Top" Width="120" ItemsSource="{Binding}">  
                <ComboBoxItem>item1</ComboBoxItem>  
                <ComboBoxItem>item2</ComboBoxItem>  
            </ComboBox>  
        </Grid>  
    </sap:ActivityDesigner>  
    ```  
  
4.  <span data-ttu-id="ea6b7-125">Créez un élément de type <xref:System.Activities.CodeActivity>.</span><span class="sxs-lookup"><span data-stu-id="ea6b7-125">Create a new item of type <xref:System.Activities.CodeActivity>.</span></span> <span data-ttu-id="ea6b7-126">Le code par défaut créé par l'IDE pour l'activité suffira pour cet exemple.</span><span class="sxs-lookup"><span data-stu-id="ea6b7-126">The default code created by the IDE for the activity will be sufficient for this example.</span></span>  
  
5.  <span data-ttu-id="ea6b7-127">Ajoutez l'attribut suivant à la définition de classe :</span><span class="sxs-lookup"><span data-stu-id="ea6b7-127">Add the following attribute to the class definition:</span></span>  
  
    ```  
    [Designer(typeof(CustomPropertyDesigner))]  
    ```  
  
     <span data-ttu-id="ea6b7-128">Cette ligne associe le nouveau concepteur à la nouvelle classe.</span><span class="sxs-lookup"><span data-stu-id="ea6b7-128">This line associates the new designer with the new class.</span></span>  
  
 <span data-ttu-id="ea6b7-129">La nouvelle activité doit maintenant être associée au concepteur.</span><span class="sxs-lookup"><span data-stu-id="ea6b7-129">The new activity should now be associated with the designer.</span></span> <span data-ttu-id="ea6b7-130">Pour tester la nouvelle activité, ajoutez-la à un workflow et affectez les deux valeurs à la zone de liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="ea6b7-130">To test the new activity, add it to a workflow, and set the combo box to the two values.</span></span> <span data-ttu-id="ea6b7-131">La fenêtre de propriétés doit être mise à jour pour refléter la valeur de la zone de liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="ea6b7-131">The properties window should update to reflect the combo box value.</span></span>
