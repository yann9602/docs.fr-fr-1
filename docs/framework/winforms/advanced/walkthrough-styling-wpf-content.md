---
title: "Procédure pas à pas : application de styles au contenu WPF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WPF Designer [Windows Forms], styling WPF content
- interoperability [WDF]
- styles [Windows Forms], WPF content
ms.assetid: e574aac7-7ea4-4cdb-8034-bab541f000df
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0fa4772ebb321f927087fe13d0d50a6ae8145e55
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-styling-wpf-content"></a>Procédure pas à pas : application de styles au contenu WPF
Cette procédure pas à pas montre comment appliquer des styles à un contrôle WPF (Windows Presentation Foundation) hébergé sur un Windows Form.  
  
 Lors de cette procédure pas à pas, vous allez exécuter les tâches suivantes :  
  
-   créer le projet ;  
  
-   créer le type de contrôle WPF ;  
  
-   appliquer un style au contrôle WPF.  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="prerequisites"></a>Prérequis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   [!INCLUDE[vs_dev11_long](../../../../includes/vs-dev11-long-md.md)].  
  
## <a name="creating-the-project"></a>Création du projet  
 La première étape consiste à créer le projet Windows Forms.  
  
> [!NOTE]
>  Lors de l'hébergement de contenu WPF, seuls les projets Visual Basic et C# sont pris en charge.  
  
#### <a name="to-create-the-project"></a>Pour créer le projet  
  
-   Créer un nouveau projet d’Application Windows Forms dans Visual Basic ou Visual c# nommé `StylingWpfContent`.  
  
## <a name="creating-the-wpf-control-types"></a>Création des types de contrôles WPF  
 Une fois que vous avez ajouté un type de contrôle WPF au projet, vous pouvez l'héberger dans un contrôle <xref:System.Windows.Forms.Integration.ElementHost>.  
  
#### <a name="to-create-wpf-control-types"></a>Pour créer des types de contrôles WPF  
  
1.  Ajoutez un nouveau projet <xref:System.Windows.Controls.UserControl> WPF à la solution. Utilisez le nom par défaut pour le type de contrôle, `UserControl1.xaml`. Pour plus d’informations, consultez [procédure pas à pas : création WPF de contenu dans les Windows Forms au moment du Design](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).  
  
2.  En mode Design, assurez-vous que `UserControl1` est sélectionné. Pour plus d’informations, consultez [Comment : sélectionner et déplacer des éléments sur l’aire de conception](http://msdn.microsoft.com/en-us/54cb70b6-b35b-46e4-a0cc-65189399c474).  
  
3.  Dans le **propriétés** fenêtre, définissez la valeur de la <xref:System.Windows.FrameworkElement.Width%2A> et <xref:System.Windows.FrameworkElement.Height%2A> propriétés `200`.  
  
4.  Ajouter un <xref:System.Windows.Controls.Button?displayProperty=nameWithType> le contrôle à la <xref:System.Windows.Controls.UserControl> et définissez la valeur de la <xref:System.Windows.Controls.ContentControl.Content%2A> propriété **Annuler**.  
  
5.  Ajoutez un deuxième <xref:System.Windows.Controls.Button?displayProperty=nameWithType> le contrôle à la <xref:System.Windows.Controls.UserControl> et définissez la valeur de la <xref:System.Windows.Controls.ContentControl.Content%2A> propriété **OK**.  
  
6.  Générez le projet.  
  
## <a name="applying-a-style-to-a-wpf-control"></a>Application d'un style à un contrôle WPF  
 Vous pouvez appliquer différents styles à un contrôle WPF pour modifier son apparence et son comportement.  
  
#### <a name="to-apply-a-style-to-a-wpf-control"></a>Pour appliquer un style à un contrôle WPF  
  
1.  Ouvrez `Form1` dans le Concepteur Windows Forms.  
  
2.  Dans le **boîte à outils**, double-cliquez sur `UserControl1` pour créer une instance de `UserControl1` sur le formulaire.  
  
     Une instance de `UserControl1` est hébergée dans un nouveau contrôle <xref:System.Windows.Forms.Integration.ElementHost> nommé `elementHost1`.  
  
3.  Dans le panneau des balises actives pour `elementHost1`, cliquez sur **modifier le contenu hébergé** dans la liste déroulante.  
  
     `UserControl1` s'ouvre dans le [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].  
  
4.  En mode XAML, insérez le code XAML suivant après la balise d'ouverture `<UserControl>`.  
  
     Ce code XAML crée un dégradé avec une bordure de dégradé contrastée. Quand l'utilisateur clique sur le contrôle, les dégradés sont modifiés pour générer une apparence de bouton enfoncé. Pour plus d’informations, consultez [Application d’un style et création de modèles](../../../../docs/framework/wpf/controls/styling-and-templating.md).  
  
```xaml  
<UserControl.Resources>  
    <LinearGradientBrush x:Key="NormalBrush" EndPoint="0,1" StartPoint="0,0">  
        <GradientStop Color="#FFF" Offset="0.0"/>  
        <GradientStop Color="#CCC" Offset="1.0"/>  
    </LinearGradientBrush>  
    <LinearGradientBrush x:Key="PressedBrush" EndPoint="0,1" StartPoint="0,0">  
        <GradientStop Color="#BBB" Offset="0.0"/>  
        <GradientStop Color="#EEE" Offset="0.1"/>  
        <GradientStop Color="#EEE" Offset="0.9"/>  
        <GradientStop Color="#FFF" Offset="1.0"/>  
    </LinearGradientBrush>  
    <LinearGradientBrush x:Key="NormalBorderBrush" EndPoint="0,1" StartPoint="0,0">  
        <GradientStop Color="#CCC" Offset="0.0"/>  
        <GradientStop Color="#444" Offset="1.0"/>  
    </LinearGradientBrush>  
    <LinearGradientBrush x:Key="BorderBrush" EndPoint="0,1" StartPoint="0,0">  
        <GradientStop Color="#CCC" Offset="0.0"/>  
        <GradientStop Color="#444" Offset="1.0"/>  
    </LinearGradientBrush>  
    <LinearGradientBrush x:Key="PressedBorderBrush" EndPoint="0,1" StartPoint="0,0">  
        <GradientStop Color="#444" Offset="0.0"/>  
        <GradientStop Color="#888" Offset="1.0"/>  
    </LinearGradientBrush>  
  
    <Style x:Key="SimpleButton" TargetType="{x:Type Button}" BasedOn="{x:Null}">  
        <Setter Property="Background" Value="{StaticResource NormalBrush}"/>  
        <Setter Property="BorderBrush" Value="{StaticResource NormalBorderBrush}"/>  
        <Setter Property="Template">  
            <Setter.Value>  
                <ControlTemplate TargetType="{x:Type Button}">  
                    <Grid x:Name="Grid">  
                        <Border x:Name="Border" Background="{TemplateBinding Background}" BorderBrush="{TemplateBinding BorderBrush}" BorderThickness="{TemplateBinding BorderThickness}" Padding="{TemplateBinding Padding}"/>  
                        <ContentPresenter HorizontalAlignment="{TemplateBinding HorizontalContentAlignment}" Margin="{TemplateBinding Padding}" VerticalAlignment="{TemplateBinding VerticalContentAlignment}" RecognizesAccessKey="True"/>  
                    </Grid>  
                    <ControlTemplate.Triggers>  
                        <Trigger Property="IsPressed" Value="true">  
                            <Setter Property="Background" Value="{StaticResource PressedBrush}" TargetName="Border"/>  
                            <Setter Property="BorderBrush" Value="{StaticResource PressedBorderBrush}" TargetName="Border"/>  
                        </Trigger>  
                    </ControlTemplate.Triggers>  
                </ControlTemplate>  
            </Setter.Value>  
        </Setter>  
    </Style>  
</UserControl.Resources>  
```  
  
1.  Appliquez le style `SimpleButton` défini à l'étape précédente au bouton Annuler en insérant le code XAML suivant dans la balise `<Button>` du bouton Annuler.  
  
    ```  
    Style="{StaticResource SimpleButton}  
    ```  
  
     Votre déclaration de bouton ressemblera au code XAML suivant.  
  
```xaml  
<Button Height="23" Margin="41,52,98,0" Name="button1" VerticalAlignment="Top"  
                Style="{StaticResource SimpleButton}">Cancel</Button>  
```  
  
1.  Générez le projet.  
  
2.  Ouvrez `Form1` dans le Concepteur Windows Forms.  
  
3.  Le nouveau style est appliqué au contrôle de bouton.  
  
4.  À partir de la **déboguer** menu, sélectionnez **démarrer le débogage** pour exécuter l’application.  
  
5.  Cliquez sur les boutons OK et Annuler et observez les différences.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [Migration et interopérabilité](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 [Utilisation de contrôles WPF](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)  
 [Concepteur WPF](http://msdn.microsoft.com/en-us/c6c65214-8411-4e16-b254-163ed4099c26)  
 [Vue d’ensemble du langage XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [Application d’un style et création de modèles](../../../../docs/framework/wpf/controls/styling-and-templating.md)
