---
title: "Proc&#233;dure pas &#224; pas&#160;: application de styles au contenu WPF | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "interopérabilité (WDF)"
  - "styles, contenu WPF"
  - "concepteur WPF, appliquer un style à un contenu WPF"
ms.assetid: e574aac7-7ea4-4cdb-8034-bab541f000df
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# Proc&#233;dure pas &#224; pas&#160;: application de styles au contenu WPF
Cette procédure pas à pas montre comment appliquer des styles à un contrôle WPF \(Windows Presentation Foundation\) hébergé sur un Windows Form.  
  
 Lors de cette procédure pas à pas, vous allez exécuter les tâches suivantes :  
  
-   créer le projet ;  
  
-   créer le type de contrôle WPF ;  
  
-   appliquer un style au contrôle WPF.  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.  Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils**.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Composants requis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   [!INCLUDE[vs_dev11_long](../../../../includes/vs-dev11-long-md.md)].  
  
## Création du projet  
 La première étape consiste à créer le projet Windows Forms.  
  
> [!NOTE]
>  Lors de l'hébergement de contenu WPF, seuls les projets Visual Basic et C\# sont pris en charge.  
  
#### Pour créer le projet  
  
-   Créez un projet d'application Windows Forms dans Visual Basic ou Visual C\# nommé `StylingWpfContent`.  
  
## Création des types de contrôles WPF  
 Une fois que vous avez ajouté un type de contrôle WPF au projet, vous pouvez l'héberger dans un contrôle <xref:System.Windows.Forms.Integration.ElementHost>.  
  
#### Pour créer des types de contrôles WPF  
  
1.  Ajoutez un nouveau projet <xref:System.Windows.Controls.UserControl> WPF à la solution.  Utilisez le nom par défaut pour le type de contrôle, `UserControl1.xaml`.  Pour plus d'informations, consultez [Procédure pas à pas : création de contenu WPF sur les Windows Forms au moment du design](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).  
  
2.  En mode Design, assurez\-vous que `UserControl1` est sélectionné.  Pour plus d'informations, consultez [Comment : sélectionner et déplacer des éléments sur l'aire de conception](http://msdn.microsoft.com/fr-fr/54cb70b6-b35b-46e4-a0cc-65189399c474).  
  
3.  Dans la fenêtre **Propriétés**, affectez la valeur `200` aux propriétés <xref:System.Windows.FrameworkElement.Width%2A> et <xref:System.Windows.FrameworkElement.Height%2A>.  
  
4.  Ajoutez un contrôle <xref:System.Windows.Controls.Button?displayProperty=fullName> au <xref:System.Windows.Controls.UserControl> et affectez la valeur Annuler à la propriété <xref:System.Windows.Controls.ContentControl.Content%2A>.  
  
5.  Ajoutez un deuxième contrôle <xref:System.Windows.Controls.Button?displayProperty=fullName> au <xref:System.Windows.Controls.UserControl> et affectez la valeur OK à la propriété <xref:System.Windows.Controls.ContentControl.Content%2A>.  
  
6.  Générez le projet.  
  
## Application d'un style à un contrôle WPF  
 Vous pouvez appliquer différents styles à un contrôle WPF pour modifier son apparence et son comportement.  
  
#### Pour appliquer un style à un contrôle WPF  
  
1.  Ouvrez `Form1` dans le Concepteur Windows Forms.  
  
2.  Dans la **Boîte à outils**, double\-cliquez sur `UserControl1` pour créer une instance de `UserControl1` sur le formulaire.  
  
     Une instance de `UserControl1` est hébergée dans un nouveau contrôle <xref:System.Windows.Forms.Integration.ElementHost> nommé `elementHost1`.  
  
3.  Dans le panneau des Smart Tags pour `elementHost1`, cliquez sur **Modifier le contenu hébergé** dans la liste déroulante.  
  
     `UserControl1` s'ouvre dans le [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].  
  
4.  En mode XAML, insérez le code XAML suivant après la balise d'ouverture `<UserControl>`.  
  
     Ce code XAML crée un dégradé avec une bordure de dégradé contrastée.  Quand l'utilisateur clique sur le contrôle, les dégradés sont modifiés pour générer une apparence de bouton enfoncé.  Pour plus d'informations, consultez [Application d'un style et création de modèles](../../../../docs/framework/wpf/controls/styling-and-templating.md).  
  
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
  
4.  Dans le menu **Débogage**, sélectionnez **Démarrer le débogage** pour exécuter l'application.  
  
5.  Cliquez sur les boutons OK et Annuler et observez les différences.  
  
## Voir aussi  
 <xref:System.Windows.Forms.Integration.ElementHost>   
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>   
 [Migration et interopérabilité](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)   
 [Utilisation de contrôles WPF](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)   
 [Concepteur WPF](http://msdn.microsoft.com/fr-fr/c6c65214-8411-4e16-b254-163ed4099c26)   
 [Vue d'ensemble du langage XAML \(WPF\)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)   
 [Application d'un style et création de modèles](../../../../docs/framework/wpf/controls/styling-and-templating.md)