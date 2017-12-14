---
title: "Procédure pas à pas : créer un bouton avec XAML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: buttons [WPF]
ms.assetid: 138c41c4-1759-4bbf-8d77-77031a06a8a0
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 543e6496c826c864dc77e50fd096fc4cb43f600e
ms.sourcegitcommit: 01ea3686e74ff05e4f6de3d8d46dc603d051ec00
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/13/2017
---
# <a name="walkthrough-create-a-button-by-using-xaml"></a>Procédure pas à pas : créer un bouton avec XAML
L’objectif de cette procédure pas à pas est d’apprendre à créer un bouton animé à utiliser dans un [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] application. Cette procédure pas à pas utilise des styles et un modèle pour créer une ressource de bouton personnalisé qui permet la réutilisation du code et la séparation de la logique de bouton de la déclaration de bouton. Cette procédure pas à pas est écrite entièrement en [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].  
  
> [!IMPORTANT]
>  Cette procédure pas à pas vous guide tout au long des étapes de création de l’application en tapant ou en copiant et en collant [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] dans Microsoft [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)]. Si vous préférez apprendre à utiliser un outil de conception (Microsoft Expression Blend) pour créer la même application, consultez [créer un bouton à l’aide de Microsoft Expression Blend](../../../../docs/framework/wpf/controls/walkthrough-create-a-button-by-using-microsoft-expression-blend.md).  
  
 L’illustration suivante montre les boutons terminés.  
  
 ![Boutons personnalisés qui ont été créés à l’aide de XAML](../../../../docs/framework/wpf/controls/media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")  
  
## <a name="create-basic-buttons"></a>Créer des boutons de base  
 Commençons par créer un nouveau projet et ajouter quelques boutons à la fenêtre.  
  
#### <a name="to-create-a-new-wpf-project-and-add-buttons-to-the-window"></a>Pour créer un projet WPF et ajouter des boutons à la fenêtre  
  
1.  Démarrer[!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)].  
  
2.  **Créez un projet WPF :** sur la **fichier** menu, pointez sur **nouveau**, puis cliquez sur **projet**. Rechercher les **Application WPF (Windows)** modèle et du nom du projet « BoutonAnimé ». Cela créera la structure de l’application.  
  
3.  **Ajouter des boutons de base par défaut :** tous les fichiers que vous avez besoin pour cette procédure pas à pas sont fournies par le modèle. Ouvrez le fichier Window1.xaml en double-cliquant dessus dans l’Explorateur de solutions. Par défaut, il existe un <xref:System.Windows.Controls.Grid> élément dans Window1.xaml. Supprimer le <xref:System.Windows.Controls.Grid> élément et ajoutez quelques boutons à la [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] page en tapant ou en copiant et collant le code en surbrillance suivant dans Window1.xaml :  
  
    ```xaml  
    <Window x:Class="AnimatedButton.Window1"  
      xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
      xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
      Title="AnimatedButton" Height="300" Width="300"   
      Background="Black">   <!-- Buttons arranged vertically inside a StackPanel. -->   <StackPanel HorizontalAlignment="Left">     <Button>Button 1</Button>     <Button>Button 2</Button>     <Button>Button 3</Button>   </StackPanel>  
  
    </Window>  
    ```  
  
     Appuyez sur F5 pour exécuter l’application ; Vous devez voir un ensemble de boutons qui ressemble à la figure suivante.  
  
     ![Trois boutons de base](../../../../docs/framework/wpf/controls/media/custom-button-animatedbutton-1.gif "custom_button_AnimatedButton_1")  
  
     Maintenant que vous avez créé les boutons de base, vous avez terminé de travailler dans le fichier Window1.xaml. Le reste de la procédure pas à pas se concentre sur le fichier app.xaml, en définissant des styles et un modèle pour les boutons.  
  
## <a name="set-basic-properties"></a>Définir les propriétés de base  
 Ensuite, nous allons définir certaines propriétés sur ces boutons pour contrôler l’apparence du bouton et la disposition. Au lieu de définir les propriétés sur les boutons individuellement, vous allez utiliser des ressources pour définir les propriétés d’un bouton pour toute l’application. Ressources d’application sont conceptuellement semblables à externe [!INCLUDE[TLA#tla_css](../../../../includes/tlasharptla-css-md.md)] pour les pages Web ; Cependant, les ressources sont beaucoup plus puissantes que [!INCLUDE[TLA#tla_css](../../../../includes/tlasharptla-css-md.md)], comme vous le verrez à la fin de cette procédure pas à pas. Pour en savoir plus sur les ressources, consultez [ressources XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md).  
  
#### <a name="to-use-styles-to-set-basic-properties-on-the-buttons"></a>Pour utiliser des styles pour définir les propriétés de base sur les boutons  
  
1.  **Définir un bloc Application.Resources :** Ouvrez app.xaml et ajoutez la balise en surbrillance suivante si elle n’est pas déjà :  
  
    ```xaml  
    <Application x:Class="AnimatedButton.App"  
      xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
      xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
      StartupUri="Window1.xaml"  
      >  
      <Application.Resources>
        <!-- Resources for the entire application can be defined here. -->
      </Application.Resources>  
    </Application>  
    ```  
  
     Portée de la ressource est déterminée par où vous définissez la ressource. Définition des ressources dans `Application.Resources` dans le app.xaml fichier permet à la ressource à utiliser à partir de n’importe où dans l’application. Pour en savoir plus sur la définition de la portée de vos ressources, consultez [ressources XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md).  
  
2.  **Créer un style et définir des valeurs de propriété de base avec lui :** ajoutez le balisage suivant à la `Application.Resources` bloc. Cette balise crée un <xref:System.Windows.Style> qui s’applique à tous les boutons dans l’application, en définissant le <xref:System.Windows.FrameworkElement.Width%2A> des boutons à 90 et <xref:System.Windows.FrameworkElement.Margin%2A> à 10 :  
  
    ```xaml  
    <Application.Resources>  
      <Style TargetType="Button">
        <Setter Property="Width" Value="90" />
        <Setter Property="Margin" Value="10" />
      </Style>  
    </Application.Resources>  
    ```  
  
     Le <xref:System.Windows.Style.TargetType%2A> propriété spécifie que le style s’applique à tous les objets de type <xref:System.Windows.Controls.Button>. Chaque <xref:System.Windows.Setter> définit une valeur de propriété différente pour le <xref:System.Windows.Style>. Par conséquent, à ce stade chaque bouton de l’application a une largeur de 90 et une marge de 10.  Si vous appuyez sur F5 pour exécuter l’application, vous voyez la fenêtre suivante.  
  
     ![Boutons avec une largeur de 90 et une marge de 10](../../../../docs/framework/wpf/controls/media/custom-button-animatedbutton-2.gif "custom_button_AnimatedButton_2")  
  
     Il est beaucoup plus que faire avec les styles, y compris les diverses méthodes permettant d’affiner quels objets sont ciblés, en spécifiant les valeurs de propriété complexe et même à l’aide de styles comme entrée pour d’autres styles. Pour plus d’informations, consultez [Application d’un style et création de modèles](../../../../docs/framework/wpf/controls/styling-and-templating.md).  
  
3.  **Valeur de propriété de style à une ressource :** ressources activer un moyen simple de réutiliser des objets couramment définis et valeurs. Il est particulièrement utile définir des valeurs complexes à l’aide des ressources pour rendre votre code plus modulaire. Ajoutez la balise en surbrillance suivante à app.xaml.  
  
    ```xaml  
    <Application.Resources>  
      <LinearGradientBrush x:Key="GrayBlueGradientBrush" StartPoint="0,0" EndPoint="1,1">
        <GradientStop Color="DarkGray" Offset="0" />
        <GradientStop Color="#CCCCFF" Offset="0.5" />
        <GradientStop Color="DarkGray" Offset="1" />
      </LinearGradientBrush>  
      <Style TargetType="{x:Type Button}">  
        <Setter Property="Background" Value="{StaticResource GrayBlueGradientBrush}" />  
        <Setter Property="Width" Value="80" />  
        <Setter Property="Margin" Value="10" />  
      </Style>  
    </Application.Resources>  
    ```  
  
     Directement sous le `Application.Resources` bloc, vous avez créé une ressource appelée « GrayBlueGradientBrush ». Ressource qui définit un dégradé horizontal. Cette ressource peut être utilisée comme une valeur de propriété à partir de n’importe où dans l’application, y compris à l’intérieur de la méthode setter style de bouton de la <xref:System.Windows.Controls.Control.Background%2A> propriété. Maintenant, tous les boutons ont une <xref:System.Windows.Controls.Control.Background%2A> valeur de la propriété de ce gradient.  
  
     Appuyez sur F5 pour exécuter l'application. Il doit se présenter comme suit.  
  
     ![Boutons avec un arrière-plan dégradé](../../../../docs/framework/wpf/controls/media/custom-button-animatedbutton-3.gif "custom_button_AnimatedButton_3")  
  
## <a name="create-a-template-that-defines-the-look-of-the-button"></a>Créer un modèle qui définit l’apparence du bouton  
 Dans cette section, vous créez un modèle qui personnalise l’apparence (présentation) du bouton. La présentation du bouton est composée de plusieurs objets, y compris des rectangles et autres composants afin de donner le bouton une apparence unique.  
  
 Jusqu'à présent, le contrôle de l’apparence des boutons dans l’application a été limité à la modification des propriétés du bouton. Que se passe-t-il si vous souhaitez apporter des modifications plus radicales à l’apparence du bouton ? Les modèles permettent un contrôle puissant sur la présentation d’un objet. Étant donné que les modèles peuvent être utilisés dans les styles, vous pouvez appliquer un modèle à tous les objets que le style s’applique (dans cette procédure pas à pas, le bouton).  
  
#### <a name="to-use-the-template-to-define-the-look-of-the-button"></a>Pour utiliser le modèle pour définir l’apparence du bouton  
  
1.  **Définir le modèle :** , car les contrôles comme <xref:System.Windows.Controls.Button> ont un <xref:System.Windows.Controls.Control.Template%2A> propriété, vous pouvez définir la valeur de propriété de modèle à l’instar des autres valeurs de propriétés que nous avons défini dans un <xref:System.Windows.Style> à l’aide un <xref:System.Windows.Setter>. Ajoutez le balisage mis en surbrillance suivant à votre style de bouton.  
  
    ```xaml
    <Application.Resources>  
      <LinearGradientBrush x:Key="GrayBlueGradientBrush"   
        StartPoint="0,0" EndPoint="1,1">  
        <GradientStop Color="DarkGray" Offset="0" />  
        <GradientStop Color="#CCCCFF" Offset="0.5" />  
        <GradientStop Color="DarkGray" Offset="1" />  
      </LinearGradientBrush>  
      <Style TargetType="{x:Type Button}">  
        <Setter Property="Background" Value="{StaticResource GrayBlueGradientBrush}" />  
        <Setter Property="Width" Value="80" />  
        <Setter Property="Margin" Value="10" />  
        <Setter Property="Template">
          <Setter.Value>
            <!-- The button template is defined here. -->
          </Setter.Value>
        </Setter>  
      </Style>  
    </Application.Resources>  
    ```  
  
2.  **Modifier la présentation de bouton :** à ce stade, vous devez définir le modèle. Ajoutez le balisage mis en surbrillance suivant. Cette balise spécifie deux <xref:System.Windows.Shapes.Rectangle> éléments avec des bords arrondis, suivi d’un <xref:System.Windows.Controls.DockPanel>. Le <xref:System.Windows.Controls.DockPanel> est utilisé pour héberger le <xref:System.Windows.Controls.ContentPresenter> du bouton. A <xref:System.Windows.Controls.ContentPresenter> affiche le contenu du bouton. Dans cette procédure pas à pas, le contenu est le texte (« Bouton 1 », « Bouton 2 », « Bouton 3 »). Tous les composants de modèle (rectangles et les <xref:System.Windows.Controls.DockPanel>) sont placés à l’intérieur d’un <xref:System.Windows.Controls.Grid>.  
  
    ```xaml  
    <Setter.Value>  
      <ControlTemplate TargetType="Button">
        <Grid Width="{TemplateBinding Width}" Height="{TemplateBinding Height}" ClipToBounds="True">
          <!-- Outer Rectangle with rounded corners. -->
          <Rectangle x:Name="outerRectangle" HorizontalAlignment="Stretch" VerticalAlignment="Stretch" Stroke="{TemplateBinding Background}" RadiusX="20" RadiusY="20" StrokeThickness="5" Fill="Transparent" />
          <!-- Inner Rectangle with rounded corners. -->
          <Rectangle x:Name="innerRectangle" HorizontalAlignment="Stretch" VerticalAlignment="Stretch" Stroke="Transparent" StrokeThickness="20" Fill="{TemplateBinding Background}" RadiusX="20" RadiusY="20" />
          <!-- Present Content (text) of the button. -->
          <DockPanel Name="myContentPresenterDockPanel">
            <ContentPresenter x:Name="myContentPresenter" Margin="20" Content="{TemplateBinding  Content}" TextBlock.Foreground="Black" />
          </DockPanel>
        </Grid>
      </ControlTemplate>  
    </Setter.Value>  
    ```  
  
     Appuyez sur F5 pour exécuter l'application. Il doit se présenter comme suit.  
  
     ![](../../../../docs/framework/wpf/controls/media/custom-button-animatedbutton-4.gif "custom_button_AnimatedButton_4")  
  
3.  **Ajouter un effet verre au modèle :** vous allez ensuite ajouter la transparence. Tout d’abord, vous créez quelques ressources qui créent un effet de dégradé de transparence. Ajoutez ces ressources de dégradés n’importe où dans le `Application.Resources` bloc :  
  
    ```xaml  
    <Application.Resources>  
      <GradientStopCollection x:Key="MyGlassGradientStopsResource">     <GradientStop Color="WhiteSmoke" Offset="0.2" />     <GradientStop Color="Transparent" Offset="0.4" />     <GradientStop Color="WhiteSmoke" Offset="0.5" />     <GradientStop Color="Transparent" Offset="0.75" />     <GradientStop Color="WhiteSmoke" Offset="0.9" />     <GradientStop Color="Transparent" Offset="1" />   </GradientStopCollection>   <LinearGradientBrush x:Key="MyGlassBrushResource"     StartPoint="0,0" EndPoint="1,1" Opacity="0.75"     GradientStops="{StaticResource MyGlassGradientStopsResource}" />  
    <!-- Styles and other resources below here. -->  
    ```  
  
     Ces ressources sont utilisées comme le <xref:System.Windows.Shapes.Shape.Fill%2A> pour un rectangle que nous insérons dans le <xref:System.Windows.Controls.Grid> du modèle de bouton. Ajoutez le balisage mis en surbrillance suivant au modèle.  
  
    ```  
    <Setter.Value>  
      <ControlTemplate TargetType="{x:Type Button}">  
        <Grid Width="{TemplateBinding Width}" Height="{TemplateBinding Height}"  
    ClipToBounds="True">  
  
        <!-- Outer Rectangle with rounded corners. -->  
        <Rectangle x:Name="outerRectangle" HorizontalAlignment="Stretch"   
          VerticalAlignment="Stretch" Stroke="{TemplateBinding Background}"   
          RadiusX="20" RadiusY="20" StrokeThickness="5" Fill="Transparent" />  
  
        <!-- Inner Rectangle with rounded corners. -->  
        <Rectangle x:Name="innerRectangle" HorizontalAlignment="Stretch"   
          VerticalAlignment="Stretch" Stroke="Transparent" StrokeThickness="20"   
          Fill="{TemplateBinding Background}" RadiusX="20" RadiusY="20" />  
  
        <!-- Glass Rectangle -->     <Rectangle x:Name="glassCube" HorizontalAlignment="Stretch"       VerticalAlignment="Stretch"       StrokeThickness="2" RadiusX="10" RadiusY="10" Opacity="0"       Fill="{StaticResource MyGlassBrushResource}"       RenderTransformOrigin="0.5,0.5">       <Rectangle.Stroke>         <LinearGradientBrush StartPoint="0.5,0" EndPoint="0.5,1">           <LinearGradientBrush.GradientStops>             <GradientStop Offset="0.0" Color="LightBlue" />             <GradientStop Offset="1.0" Color="Gray" />           </LinearGradientBrush.GradientStops>         </LinearGradientBrush>       </Rectangle.Stroke>       <!-- These transforms have no effect as they are declared here.             The reason the transforms are included is to be targets             for animation (see later). -->       <Rectangle.RenderTransform>         <TransformGroup>           <ScaleTransform />           <RotateTransform />         </TransformGroup>       </Rectangle.RenderTransform>       <!-- A BevelBitmapEffect is applied to give the button a             "Beveled" look. -->       <Rectangle.BitmapEffect>         <BevelBitmapEffect />       </Rectangle.BitmapEffect>     </Rectangle>  
  
        <!-- Present Text of the button. -->  
        <DockPanel Name="myContentPresenterDockPanel">  
          <ContentPresenter x:Name="myContentPresenter" Margin="20"   
            Content="{TemplateBinding  Content}" TextBlock.Foreground="Black" />  
        </DockPanel>  
      </Grid>  
    </ControlTemplate>  
    </Setter.Value>  
    ```  
  
     Notez que la <xref:System.Windows.UIElement.Opacity%2A> du rectangle avec le `x:Name` propriété de « glassCube » est égal à 0, donc lorsque vous exécutez l’exemple, vous ne voyez pas le rectangle transparent à superposer sur le haut. Il s’agit, car nous ajouterons ultérieurement des déclencheurs dans le modèle pour lorsque l’utilisateur interagit avec le bouton. Toutefois, vous pouvez voir à quoi ressemble le bouton en modifiant la <xref:System.Windows.UIElement.Opacity%2A> valeur sur 1 et de l’application en cours d’exécution. Voir l'illustration suivante. Avant de passer à l’étape suivante, modifiez le <xref:System.Windows.UIElement.Opacity%2A> à 0.  
  
     ![Boutons personnalisés qui ont été créés à l’aide de XAML](../../../../docs/framework/wpf/controls/media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")  
  
## <a name="create-button-interactivity"></a>Créer l’interactivité de bouton  
 Dans cette section, vous allez créer des déclencheurs de propriété et modifier les valeurs de propriété et exécuter des animations en réponse aux actions utilisateur telles que le déplacement du pointeur de la souris sur le bouton, puis en cliquant sur les déclencheurs d’événements.  
  
 Un moyen simple pour ajouter une interactivité (pointage avec la souris, éloignement de la souris, cliquez sur et ainsi de suite) consiste à définir des déclencheurs au sein de votre modèle ou un style. Pour créer un <xref:System.Windows.Trigger>, vous définissez une propriété « condition » telles que : le bouton <xref:System.Windows.UIElement.IsMouseOver%2A> valeur de propriété est égale à `true`. Vous définissez ensuite les accesseurs Set (actions) qui ont lieu lorsque la condition de déclenchement est true.  
  
#### <a name="to-create-button-interactivity"></a>Pour créer l’interactivité de bouton  
  
1.  **Ajouter des déclencheurs de modèle :** ajouter le balisage mis en surbrillance à votre modèle.  
  
    ```  
    <Setter.Value>  
      <ControlTemplate TargetType="{x:Type Button}">  
        <Grid Width="{TemplateBinding Width}"   
          Height="{TemplateBinding Height}" ClipToBounds="True">  
  
          <!-- Outer Rectangle with rounded corners. -->  
          <Rectangle x:Name="outerRectangle" HorizontalAlignment="Stretch"   
          VerticalAlignment="Stretch" Stroke="{TemplateBinding Background}"   
          RadiusX="20" RadiusY="20" StrokeThickness="5" Fill="Transparent" />  
  
          <!-- Inner Rectangle with rounded corners. -->  
          <Rectangle x:Name="innerRectangle" HorizontalAlignment="Stretch"   
            VerticalAlignment="Stretch" Stroke="Transparent"   
            StrokeThickness="20"   
            Fill="{TemplateBinding Background}" RadiusX="20" RadiusY="20"   
          />  
  
          <!-- Glass Rectangle -->  
          <Rectangle x:Name="glassCube" HorizontalAlignment="Stretch"  
            VerticalAlignment="Stretch"  
            StrokeThickness="2" RadiusX="10" RadiusY="10" Opacity="0"  
            Fill="{StaticResource MyGlassBrushResource}"  
            RenderTransformOrigin="0.5,0.5">  
            <Rectangle.Stroke>  
              <LinearGradientBrush StartPoint="0.5,0" EndPoint="0.5,1">  
                <LinearGradientBrush.GradientStops>  
                  <GradientStop Offset="0.0" Color="LightBlue" />  
                  <GradientStop Offset="1.0" Color="Gray" />  
                </LinearGradientBrush.GradientStops>  
              </LinearGradientBrush>  
            </Rectangle.Stroke>  
  
            <!-- These transforms have no effect as they   
                 are declared here.   
                 The reason the transforms are included is to be targets   
                 for animation (see later). -->  
            <Rectangle.RenderTransform>  
              <TransformGroup>  
                <ScaleTransform />  
                <RotateTransform />  
              </TransformGroup>  
            </Rectangle.RenderTransform>  
  
              <!-- A BevelBitmapEffect is applied to give the button a   
                   "Beveled" look. -->  
            <Rectangle.BitmapEffect>  
              <BevelBitmapEffect />  
            </Rectangle.BitmapEffect>  
          </Rectangle>  
  
          <!-- Present Text of the button. -->  
          <DockPanel Name="myContentPresenterDockPanel">  
            <ContentPresenter x:Name="myContentPresenter" Margin="20"   
              Content="{TemplateBinding  Content}" TextBlock.Foreground="Black" />  
          </DockPanel>  
        </Grid>  
  
        <ControlTemplate.Triggers>       <!-- Set action triggers for the buttons and define            what the button does in response to those triggers. -->     </ControlTemplate.Triggers>  
      </ControlTemplate>  
    </Setter.Value>  
    ```  
  
2.  **Ajouter des déclencheurs de propriété :** ajoutez le balisage mis en surbrillance à le `ControlTemplate.Triggers` bloc :  
  
    ```  
    <ControlTemplate.Triggers>  
  
      <!-- Set properties when mouse pointer is over the button. -->   <Trigger Property="IsMouseOver" Value="True">     <!-- Below are three property settings that occur when the           condition is met (user mouses over button).  -->     <!-- Change the color of the outer rectangle when user           mouses over it. -->     <Setter Property ="Rectangle.Stroke" TargetName="outerRectangle"       Value="{DynamicResource {x:Static SystemColors.HighlightBrushKey}}" />     <!-- Sets the glass opacity to 1, therefore, the           glass "appears" when user mouses over it. -->     <Setter Property="Rectangle.Opacity" Value="1" TargetName="glassCube" />     <!-- Makes the text slightly blurry as though you           were looking at it through blurry glass. -->     <Setter Property="ContentPresenter.BitmapEffect"        TargetName="myContentPresenter">       <Setter.Value>         <BlurBitmapEffect Radius="1" />       </Setter.Value>     </Setter>   </Trigger>  
  
    <ControlTemplate.Triggers/>  
    ```  
  
     Appuyez sur F5 pour exécuter l’application et voir l’effet lorsque vous exécutez le pointeur de la souris sur les boutons.  
  
3.  **Ajouter un déclencheur de focus :** ensuite, nous allons ajouter certains setters similaire pour gérer le cas lorsque le bouton est activé (par exemple, une fois que l’utilisateur clique dessus).  
  
    ```  
    <ControlTemplate.Triggers>  
  
      <!-- Set properties when mouse pointer is over the button. -->  
      <Trigger Property="IsMouseOver" Value="True">  
  
        <!-- Below are three property settings that occur when the   
             condition is met (user mouses over button).  -->  
        <!-- Change the color of the outer rectangle when user          mouses over it. -->  
        <Setter Property ="Rectangle.Stroke" TargetName="outerRectangle"  
          Value="{DynamicResource {x:Static SystemColors.HighlightBrushKey}}" />  
  
        <!-- Sets the glass opacity to 1, therefore, the          glass "appears" when user mouses over it. -->  
        <Setter Property="Rectangle.Opacity" Value="1"       TargetName="glassCube" />  
  
        <!-- Makes the text slightly blurry as though you were          looking at it through blurry glass. -->  
        <Setter Property="ContentPresenter.BitmapEffect"       TargetName="myContentPresenter">  
          <Setter.Value>  
            <BlurBitmapEffect Radius="1" />  
          </Setter.Value>  
        </Setter>  
      </Trigger>  
      <!-- Set properties when button has focus. -->   <Trigger Property="IsFocused" Value="true">     <Setter Property="Rectangle.Opacity" Value="1"       TargetName="glassCube" />     <Setter Property="Rectangle.Stroke" TargetName="outerRectangle"       Value="{DynamicResource {x:Static SystemColors.HighlightBrushKey}}" />     <Setter Property="Rectangle.Opacity" Value="1" TargetName="glassCube" />   </Trigger>  
  
    </ControlTemplate.Triggers>  
    ```  
  
     Appuyez sur F5 pour exécuter l’application et cliquez sur un des boutons. Notez que le bouton reste en surbrillance une fois que vous cliquez dessus, car elle a encore le focus. Si vous cliquez sur un autre, le bouton Nouveau acquiert un focus pendant que le dernier le perd.  
  
4.  **Ajouter des animations pour** <xref:System.Windows.UIElement.MouseEnter> **et** <xref:System.Windows.UIElement.MouseLeave> **:** ensuite, nous ajoutons certaines animations aux déclencheurs. Ajoutez le balisage suivant n’importe où à l’intérieur de la `ControlTemplate.Triggers` bloc.  
  
    ```  
    <!-- Animations that start when mouse enters and leaves button. -->  
    <EventTrigger RoutedEvent="Mouse.MouseEnter">  
      <EventTrigger.Actions>  
        <BeginStoryboard Name="mouseEnterBeginStoryboard">  
          <Storyboard>  
          <!-- This animation makes the glass rectangle shrink in the X direction. -->  
            <DoubleAnimation Storyboard.TargetName="glassCube"   
              Storyboard.TargetProperty=  
              "(Rectangle.RenderTransform).(TransformGroup.Children)[0].(ScaleTransform.ScaleX)"  
              By="-0.1" Duration="0:0:0.5" />  
            <!-- This animation makes the glass rectangle shrink in the Y direction. -->  
            <DoubleAnimation  
            Storyboard.TargetName="glassCube"   
              Storyboard.TargetProperty=  
              "(Rectangle.RenderTransform).(TransformGroup.Children)[0].(ScaleTransform.ScaleY)"   
              By="-0.1" Duration="0:0:0.5" />  
          </Storyboard>  
        </BeginStoryboard>  
      </EventTrigger.Actions>  
    </EventTrigger>  
    <EventTrigger RoutedEvent="Mouse.MouseLeave">  
      <EventTrigger.Actions>  
        <!-- Stopping the storyboard sets all animated properties back to default. -->  
        <StopStoryboard BeginStoryboardName="mouseEnterBeginStoryboard" />  
      </EventTrigger.Actions>  
    </EventTrigger>  
    ```  
  
     Le rectangle transparent est réduit lorsque le pointeur de la souris se déplace sur le bouton et revient à sa taille normale lorsque le pointeur quitte.  
  
     Il existe deux animations qui sont déclenchées lorsque le pointeur passe sur le bouton (<xref:System.Windows.UIElement.MouseEnter> événement est déclenché). Ces animations réduisent le rectangle transparent sur l’axe des X et Y. Notez les propriétés sur le <xref:System.Windows.Media.Animation.DoubleAnimation> éléments : <xref:System.Windows.Media.Animation.Timeline.Duration%2A> et <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>. Le <xref:System.Windows.Media.Animation.Timeline.Duration%2A> Spécifie que l’animation a lieu pendant une demi-seconde, et <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> Spécifie que le verre se réduit de 10 %.  
  
     Le deuxième déclencheur d’événement (<xref:System.Windows.UIElement.MouseLeave>) arrête simplement le premier. Lorsque vous arrêtez un <xref:System.Windows.Media.Animation.Storyboard>, toutes les propriétés animées retournent leurs valeurs par défaut. Par conséquent, lorsque l’utilisateur déplace le pointeur hors du bouton, le bouton repasse à la façon dont il était avant que le pointeur de la souris est déplacé sur le bouton. Pour plus d’informations sur les animations, consultez [vue d’ensemble de l’Animation](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).  
  
5.  **Ajouter une animation lorsque le bouton est cliqué :** l’étape finale consiste à ajouter un déclencheur lorsque l’utilisateur clique sur le bouton. Ajoutez le balisage suivant n’importe où à l’intérieur de la `ControlTemplate.Triggers` bloc :  
  
    ```  
    <!-- Animation fires when button is clicked, causing glass to spin.  -->  
    <EventTrigger RoutedEvent="Button.Click">  
      <EventTrigger.Actions>  
        <BeginStoryboard>  
          <Storyboard>  
            <DoubleAnimation Storyboard.TargetName="glassCube"   
              Storyboard.TargetProperty=  
              "(Rectangle.RenderTransform).(TransformGroup.Children)[1].(RotateTransform.Angle)"   
              By="360" Duration="0:0:0.5" />  
          </Storyboard>  
        </BeginStoryboard>  
      </EventTrigger.Actions>  
    </EventTrigger>  
    ```  
  
     Appuyez sur F5 pour exécuter l’application, puis cliquez sur un des boutons. Lorsque vous cliquez sur un bouton, le rectangle de verre tourne.  
  
## <a name="summary"></a>Résumé  
 Dans cette procédure pas à pas, vous avez effectué les exercices suivants :  
  
-   Cible un <xref:System.Windows.Style> à un type d’objet (<xref:System.Windows.Controls.Button>).  
  
-   Contrôlé des propriétés de base des boutons dans l’ensemble de l’application à l’aide de la <xref:System.Windows.Style>.  
  
-   Création des ressources telles que des dégradés à utiliser pour les valeurs de propriété de la <xref:System.Windows.Style> setters.  
  
-   Personnaliser l’apparence des boutons de l’application entière en appliquant un modèle pour les boutons.  
  
-   Personnalisé le comportement des boutons en réponse aux actions de l’utilisateur (tel que <xref:System.Windows.UIElement.MouseEnter>, <xref:System.Windows.UIElement.MouseLeave>, et <xref:System.Windows.Controls.Primitives.ButtonBase.Click>) qui inclus les effets d’animation.  
  
## <a name="see-also"></a>Voir aussi  
 [Créer un bouton à l'aide de Microsoft Expression Blend](../../../../docs/framework/wpf/controls/walkthrough-create-a-button-by-using-microsoft-expression-blend.md)  
 [Application d’un style et création de modèles](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [Vue d’ensemble de l’animation](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Vue d’ensemble de la peinture avec des couleurs unies ou des dégradés](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)  
 [Vue d’ensemble des effets bitmap](../../../../docs/framework/wpf/graphics-multimedia/bitmap-effects-overview.md)
