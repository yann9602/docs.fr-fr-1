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
ms.openlocfilehash: 07a39983d0e561fdad4c09e641912b0d15aa4033
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="binding-a-custom-activity-property-to-a-designer-control"></a>Liaison d’une propriété d’activité personnalisée à un contrôle de concepteur
La liaison contrôle de concepteur de zone de texte à un argument d'activité est assez simple . Toutefois, la liaison d'un contrôle de concepteur complexe (tel qu'une zone de liste déroulante) à un argument d'activité peut poser des problèmes. Cette rubrique explique comment lier un argument d'activité à un contrôle de zone de liste déroulante sur un concepteur d'activités personnalisées.  
  
#### <a name="creating-the-combo-box-item-converter"></a>Création du convertisseur d'éléments de zone de liste déroulante  
  
1.  Créez une solution vide appelée CustomProperty dans Visual Studio.  
  
2.  Créez une classe appelée ComboBoxItemConverter. Ajoutez une référence à System.Windows.Data et faites dériver la classe de <xref:System.Windows.Data.IValueConverter>. Faites en sorte que Visual Studio implémente l'interface pour générer des stubs pour `Convert` et `ConvertBack`.  
  
3.  Ajoutez le code suivant à la méthode `Convert`. Ce code convertit l'<xref:System.Activities.InArgument%601> de l'activité de type <xref:System.String> en la valeur à placer dans le concepteur.  
  
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
  
     L'expression dans l'extrait de code ci-dessus peut également être créée à l'aide de <xref:Microsoft.CSharp.Activities.CSharpValue%601> à la place de <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601>.  
  
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
  
4.  Ajoutez le code suivant à la méthode `ConvertBack`. Ce code convertit à nouveau l'élément de zone de liste déroulante entrant en <xref:System.Activities.InArgument%601>.  
  
    ```  
    // Convert combo box value to InArgument<string>  
                string itemContent = (string)((ComboBoxItem)value).Content;  
                VisualBasicValue<string> vbArgument = new VisualBasicValue<string>(itemContent);  
                InArgument<string> inArgument = new InArgument<string>(vbArgument);  
                return inArgument;  
    ```  
  
     L'expression dans l'extrait de code ci-dessus peut également être créée à l'aide de <xref:Microsoft.CSharp.Activities.CSharpValue%601> à la place de <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601>.  
  
    ```  
    // Convert combo box value to InArgument<string>  
                string itemContent = (string)((ComboBoxItem)value).Content;  
                CSharpValue<string> csArgument = new CSharpValue<string>(itemContent);  
                InArgument<string> inArgument = new InArgument<string>(csArgument);  
                return inArgument;  
    ```  
  
#### <a name="adding-the-comboboxitemconverter-to-the-custom-designer-of-an-activity"></a>Ajout de ComboBoxItemConverter au concepteur personnalisé d'une activité  
  
1.  Ajoutez un nouvel élément au projet. Dans la boîte de dialogue Nouvel élément, sélectionnez le nœud de workflow et ActivityDesigner comme type de nouvel élément. Nommez le CustomPropertyDesigner de l'élément.  
  
2.  Ajoutez une zone de liste déroulante au nouveau concepteur. Dans la propriété Items, ajoutez plusieurs éléments à la zone de liste déroulante, avec les valeurs de contenu « Item1 » et « Item2 ».  
  
3.  Modifiez le code XAML de la zone de liste déroulante pour ajouter le nouveau convertisseur d'éléments comme convertisseur à utiliser pour la zone de liste déroulante. Le convertisseur est ajouté comme ressource dans le segment ActivityDesigner.Resources et spécifie le convertisseur dans l'attribut Converter pour la <xref:System.Windows.Controls.ComboBox>. Notez que l'espace de noms du projet est spécifié dans les attributs Namespaces pour le concepteur d'activité ; si le concepteur doit être utilisé dans un projet différent, cet espace de noms devra être modifié.  
  
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
  
4.  Créez un élément de type <xref:System.Activities.CodeActivity>. Le code par défaut créé par l'IDE pour l'activité suffira pour cet exemple.  
  
5.  Ajoutez l'attribut suivant à la définition de classe :  
  
    ```  
    [Designer(typeof(CustomPropertyDesigner))]  
    ```  
  
     Cette ligne associe le nouveau concepteur à la nouvelle classe.  
  
 La nouvelle activité doit maintenant être associée au concepteur. Pour tester la nouvelle activité, ajoutez-la à un workflow et affectez les deux valeurs à la zone de liste déroulante. La fenêtre de propriétés doit être mise à jour pour refléter la valeur de la zone de liste déroulante.
