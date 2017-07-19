---
title: "Proc&#233;dure pas &#224; pas&#160;: cr&#233;er un bouton avec XAML | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "boutons"
ms.assetid: 138c41c4-1759-4bbf-8d77-77031a06a8a0
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# Proc&#233;dure pas &#224; pas&#160;: cr&#233;er un bouton avec XAML
L'objectif de cette procédure pas à pas est d'apprendre à créer un bouton animé à utiliser dans une application [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)].  Cette procédure pas à pas utilise des styles et un modèle pour créer une ressource de bouton personnalisée qui autorise la réutilisation de code et la séparation de la logique bouton de la déclaration de bouton.  Cette procédure pas à pas est écrite entièrement en [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].  
  
> [!IMPORTANT]
>  Cette procédure pas à pas vous guide à travers les étapes de création de l'application en tapant ou copiant et collant [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] dans Microsoft [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)].  Si vous préférez apprendre comment utiliser un outil de conception \(Microsoft Expression Blend\) pour créer la même application, consultez [Créer un bouton à l'aide de Microsoft Expression Blend](../../../../docs/framework/wpf/controls/walkthrough-create-a-button-by-using-microsoft-expression-blend.md).  
  
 L'illustration suivante montre les boutons finis.  
  
 ![Boutons personnalisés créés en utilisant XAML](../../../../docs/framework/wpf/controls/media/custom-button-animatedbutton-5.png "custom\_button\_AnimatedButton\_5")  
  
## Créer des boutons de base  
 Démarrons en créant un projet et en ajoutant quelques boutons à la fenêtre.  
  
#### Pour créer un projet WPF et ajouter des boutons à la fenêtre  
  
1.  Démarrez [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)].  
  
2.  **Créez un projet WPF :** Dans le menu **Fichier**, pointez sur **Nouveau**, puis cliquez sur **Projet**.  Recherchez le modèle d'**application Windows \(WPF\)** et nommez le projet "BoutonAnimé".  Cela créera la structure pour l'application.  
  
3.  **Ajoutez des boutons de base par défaut :** Tous les fichiers dont vous avez besoin pour cette procédure pas à pas sont fournis par le modèle.  Dans l'Explorateur de solutions, double\-cliquez sur le fichier Windows1.xaml pour l'ouvrir.  Par défaut, il y a un élément <xref:System.Windows.Controls.Grid> dans Window1.xaml.  Supprimez l'élément <xref:System.Windows.Controls.Grid> et ajoutez quelques boutons à la page [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] en tapant ou en copiant et collant le code en surbrillance suivant dans Window1.xaml :  
  
    ```  
    <Window x:Class="AnimatedButton.Window1"  
      xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
      xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
      Title="AnimatedButton" Height="300" Width="300"   
      Background="Black">  
  
      <!-- Buttons arranged vertically inside a StackPanel. -->  
      <StackPanel HorizontalAlignment="Left">  
        <Button>Button 1</Button>  
        <Button>Button 2</Button>  
        <Button>Button 3</Button>  
      </StackPanel>  
  
    </Window>  
    ```  
  
     Appuyez sur F5 pour exécuter l'application ; vous devriez voir un jeu de boutons qui ressemble à l'illustration suivante.  
  
     ![Trois boutons de base](../../../../docs/framework/wpf/controls/media/custom-button-animatedbutton-1.png "custom\_button\_AnimatedButton\_1")  
  
     Maintenant que vous avez créé les boutons de base, vous avez terminé de travailler dans le fichier Window1.xaml.  Le reste de la procédure pas à pas se concentre sur le fichier app.xaml, en définissant des styles et un modèle pour les boutons.  
  
## Définir les propriétés de base  
 Définissons maintenant quelques propriétés sur ces boutons pour contrôler leur apparence et disposition.  Plutôt que de définir des propriétés sur les boutons individuellement, vous utiliserez des ressources pour définir des propriétés de bouton pour l'application entière.  Les ressources d'application sont conceptuellement semblables au [!INCLUDE[TLA#tla_css](../../../../includes/tlasharptla-css-md.md)] externe pour les pages Web ; cependant, les ressources sont beaucoup plus puissantes que [!INCLUDE[TLA#tla_css](../../../../includes/tlasharptla-css-md.md)], comme vous le constaterez à la fin de cette procédure pas à pas.  Pour en savoir plus sur les ressources, consultez [Ressources XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md).  
  
#### Pour utiliser des styles pour définir des propriétés de base sur les boutons  
  
1.  **Définissez un bloc de ressources d'application :** Ouvrez app.xaml et ajoutez la balise en surbrillance suivante si elle n'y est pas déjà :  
  
    ```  
    <Application x:Class="AnimatedButton.App"  
      xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
      xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
      StartupUri="Window1.xaml"  
      >  
      <Application.Resources>  
  
        <!-- Resources for the entire application can be   
             defined here. -->  
  
      </Application.Resources>  
    </Application>  
    ```  
  
     La portée de la ressource est déterminée par l'endroit où vous définissez la ressource.  La définition des ressources dans `Application.Resoureses` dans le fichier app.xaml active la ressource à utiliser de n'importe où dans l'application.  Pour en savoir plus sur la définition de la portée de vos ressources, consultez [Ressources XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md).  
  
2.  **Créez un style et définissez des valeurs de propriété de base avec lui :** Ajoutez la balise suivante au bloc `Application.Resources`.  Cette balise crée un <xref:System.Windows.Style> qui s'applique à tous les boutons dans l'application, en définissant la <xref:System.Windows.FrameworkElement.Width%2A> des boutons à 90 et la <xref:System.Windows.FrameworkElement.Margin%2A> à 10 :  
  
    ```  
    <Application.Resources>  
  
      <Style TargetType="Button">  
        <Setter Property="Width" Value="90" />  
        <Setter Property="Margin" Value="10" />  
      </Style>  
  
    </Application.Resources>  
    ```  
  
     La propriété <xref:System.Windows.Style.TargetType%2A> spécifie que le style s'applique à tous les objets de type <xref:System.Windows.Controls.Button>.  Chaque <xref:System.Windows.Setter> définit une valeur de propriété différente pour le <xref:System.Windows.Style>.  Par conséquent, à ce stade, chaque bouton de l'application a une largeur de 90 et une marge de 10.  Si vous appuyez sur F5 pour exécuter l'application, vous voyez s'afficher la fenêtre suivante.  
  
     ![Boutons avec une largeur de 90 et une marge de 10](../../../../docs/framework/wpf/controls/media/custom-button-animatedbutton-2.png "custom\_button\_AnimatedButton\_2")  
  
     Vous pouvez en faire encore davantage avec les styles, y compris une variété de méthodes permettant d'affiner quels objets sont ciblés, de spécifier des valeurs de propriété complexes, et même d'utiliser des styles comme entrée pour d'autres styles.  Pour plus d'informations, consultez [Application d'un style et création de modèles](../../../../docs/framework/wpf/controls/styling-and-templating.md).  
  
3.  **Définissez une valeur de propriété de style à une ressource :** les ressources activent une méthode simple permettant de réutiliser des objets et valeurs couramment définis.  Il est particulièrement utile de définir des valeurs complexes à l'aide de ressources pour rendre votre code plus modulaire.  Ajoutez la balise en surbrillance suivante à app.xaml.  
  
    ```  
    <Application.Resources>  
  
      <LinearGradientBrush x:Key="GrayBlueGradientBrush"   
        StartPoint="0,0" EndPoint="1,1">  
        <GradientStop Color="DarkGray" Offset="0" />  
        <GradientStop Color="#CCCCFF" Offset="0.5" />  
        <GradientStop Color="DarkGray" Offset="1" />  
      </LinearGradientBrush>  
  
      <Style TargetType="{x:Type Button}">  
        <Setter Property="Background"   
          Value="{StaticResource GrayBlueGradientBrush}" />  
        <Setter Property="Width" Value="80" />  
        <Setter Property="Margin" Value="10" />  
      </Style>  
  
    </Application.Resources>  
    ```  
  
     Directement sous le bloc `Application.Resources`, vous avez créé une ressource appelée "GrayBlueGradientBrush."  Cette ressource définit un gradient horizontal.  Cette ressource peut être utilisée n'importe dans l'application comme valeur de propriété, y compris à l'intérieur de l'accesseur Set de style des boutons pour la propriété <xref:System.Windows.Controls.Control.Background%2A>.  Maintenant, tous les boutons ont une valeur de propriété <xref:System.Windows.Controls.Control.Background%2A> de ce gradient.  
  
     Appuyez sur F5 pour exécuter l'application.  Il doit se présenter comme suit.  
  
     ![Boutons avec un arrière&#45;plan dégradé](../../../../docs/framework/wpf/controls/media/custom-button-animatedbutton-3.png "custom\_button\_AnimatedButton\_3")  
  
## Créer un modèle qui définit l'apparence du bouton  
 Dans cette section, vous créez un modèle qui personnalise l'apparence \(présentation\) du bouton.  La présentation du bouton est composée de plusieurs objets, y compris des rectangles et d'autres composants, pour donner une apparence unique au bouton.  
  
 Jusqu'à présent, le contrôle de l'apparence des boutons dans l'application a été restreint à la modification des propriétés du bouton.  Et si vous souhaitez apporter des modifications plus radicales à l'apparence du bouton ?  Les modèles permettent un contrôle puissant sur la présentation d'un objet.  Les modèles pouvant être utilisés dans des styles, vous pouvez appliquer un modèle à tous les objets auxquels le style s'applique \(dans cette procédure pas à pas, le bouton\).  
  
#### Pour utiliser le modèle pour définir l'apparence du bouton  
  
1.  **Installer le modèle :** les contrôles comme <xref:System.Windows.Controls.Button> ayant une propriété <xref:System.Windows.Controls.Control.Template%2A>, vous pouvez définir la valeur de propriété de modèle comme les autres valeurs de propriété que nous avons définies dans un <xref:System.Windows.Style> à l'aide d'un <xref:System.Windows.Setter>.  Ajoutez la balise en surbrillance suivante à votre style de boutons.  
  
    ```  
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
  
2.  **Modifier la présentation de bouton :** à ce stade, vous devez définir le modèle.  Ajoutez la balise en surbrillance suivante.  Cette balise spécifie deux éléments <xref:System.Windows.Shapes.Rectangle> avec les bords arrondis, suivis par un <xref:System.Windows.Controls.DockPanel>.  Le <xref:System.Windows.Controls.DockPanel> est utilisé pour héberger le <xref:System.Windows.Controls.ContentPresenter> du bouton.  Une <xref:System.Windows.Controls.ContentPresenter> affiche le contenu du bouton.  Dans cette procédure pas à pas, le contenu est représenté par du texte \("Bouton 1", "Bouton 2", "Bouton 3"\).  Tous les composants de modèle \(rectangles et <xref:System.Windows.Controls.DockPanel>\) sont présentés dans <xref:System.Windows.Controls.Grid>.  
  
    ```  
    <Setter.Value>  
      <ControlTemplate TargetType="Button">  
        <Grid Width="{TemplateBinding Width}"   
         Height="{TemplateBinding Height}" ClipToBounds="True">  
  
          <!-- Outer Rectangle with rounded corners. -->  
          <Rectangle x:Name="outerRectangle"   
            HorizontalAlignment="Stretch"   
            VerticalAlignment="Stretch"   
            Stroke="{TemplateBinding Background}"   
            RadiusX="20" RadiusY="20" StrokeThickness="5"   
            Fill="Transparent" />  
  
          <!-- Inner Rectangle with rounded corners. -->  
          <Rectangle x:Name="innerRectangle"   
            HorizontalAlignment="Stretch"   
            VerticalAlignment="Stretch" Stroke="Transparent"   
            StrokeThickness="20"   
            Fill="{TemplateBinding Background}"   
            RadiusX="20" RadiusY="20"   />  
  
          <!-- Present Content (text) of the button. -->  
          <DockPanel Name="myContentPresenterDockPanel">  
            <ContentPresenter x:Name="myContentPresenter" Margin="20"   
              Content="{TemplateBinding  Content}"   
              TextBlock.Foreground="Black" />  
          </DockPanel>  
        </Grid>  
      </ControlTemplate>  
    </Setter.Value>  
    ```  
  
     Appuyez sur F5 pour exécuter l'application.  Il doit se présenter comme suit.  
  
     ![](../../../../docs/framework/wpf/controls/media/custom-button-animatedbutton-4.gif "custom\_button\_AnimatedButton\_4")  
  
3.  **Ajouter un effet verre au modèle :** vous ajouterez le verre après.  En premier lieu, vous créez quelques ressources qui créent un verre effet dégradé.  Ajoutez ces ressources de dégradés n'importe où dans le bloc `Application.Resources` :  
  
    ```  
    <Application.Resources>  
      <GradientStopCollection x:Key="MyGlassGradientStopsResource">  
        <GradientStop Color="WhiteSmoke" Offset="0.2" />  
        <GradientStop Color="Transparent" Offset="0.4" />  
        <GradientStop Color="WhiteSmoke" Offset="0.5" />  
        <GradientStop Color="Transparent" Offset="0.75" />  
        <GradientStop Color="WhiteSmoke" Offset="0.9" />  
        <GradientStop Color="Transparent" Offset="1" />  
      </GradientStopCollection>  
  
      <LinearGradientBrush x:Key="MyGlassBrushResource"   
       StartPoint="0,0" EndPoint="1,1" Opacity="0.75"   
       GradientStops="{StaticResource MyGlassGradientStopsResource}" />  
    <!-- Styles and other resources below here. -->  
    ```  
  
     Ces ressources sont utilisées comme <xref:System.Windows.Shapes.Shape.Fill%2A> pour un rectangle que nous insérons dans le <xref:System.Windows.Controls.Grid> du modèle de bouton.  Ajoutez la balise en surbrillance suivante au modèle.  
  
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
  
          <!-- These transforms have no effect as they are declared here.   
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
    </ControlTemplate>  
    </Setter.Value>  
    ```  
  
     Remarquez que l'<xref:System.Windows.UIElement.Opacity%2A> du rectangle avec la propriété `x:Name` de "CubeVerre" \("glassCube"\) est 0, donc lorsque vous exécutez l'exemple, vous ne voyez pas la superposition du rectangle de verre sur le dessus.  La raison est que nous ajouterons ultérieurement des déclencheurs au modèle lorsque l'utilisateur interagit avec le bouton.  Toutefois, vous pouvez voir à quoi ressemble le bouton en modifiant la valeur <xref:System.Windows.UIElement.Opacity%2A> à 1 et exécutant l'application.  Voir l'illustration suivante.  Avant de passer à l'étape suivante, modifiez l'<xref:System.Windows.UIElement.Opacity%2A> à 0.  
  
     ![Boutons personnalisés créés en utilisant XAML](../../../../docs/framework/wpf/controls/media/custom-button-animatedbutton-5.png "custom\_button\_AnimatedButton\_5")  
  
## Créer l'interactivité de bouton  
 De cette section, vous allez créer des déclencheurs de propriété et des déclencheurs d'événements pour modifier des valeurs de propriété et exécuter des animations en réponse aux actions des utilisateurs telles que le déplacement du pointeur de la souris sur le bouton et le clic.  
  
 Une méthode simple pour ajouter l'interactivité \(pointage avec la souris, éloignement de la souris, clic, etc.\) est de définir des déclencheurs dans votre modèle ou style.  Pour créer un <xref:System.Windows.Trigger>, vous définissez une "condition" de propriété telle que : la valeur de la propriété du bouton <xref:System.Windows.UIElement.IsMouseOver%2A> est égale à `true`.  Vous définissez alors des accesseurs Set \(actions\) qui ont lieu lorsque la condition de déclencheur est remplie.  
  
#### Pour créer l'interactivité de bouton  
  
1.  **Ajouter des déclencheurs de modèle :** ajoutez la balise en surbrillance à votre modèle.  
  
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
  
        <ControlTemplate.Triggers>  
          <!-- Set action triggers for the buttons and define  
               what the button does in response to those triggers. -->  
        </ControlTemplate.Triggers>  
      </ControlTemplate>  
    </Setter.Value>  
    ```  
  
2.  **Ajouter des déclencheurs de propriété :** ajoutez la balise en surbrillance au bloc `ControlTemplate.Triggers` :  
  
    ```  
    <ControlTemplate.Triggers>  
  
      <!-- Set properties when mouse pointer is over the button. -->  
      <Trigger Property="IsMouseOver" Value="True">  
  
        <!-- Below are three property settings that occur when the   
             condition is met (user mouses over button).  -->  
        <!-- Change the color of the outer rectangle when user   
             mouses over it. -->  
        <Setter Property ="Rectangle.Stroke" TargetName="outerRectangle"  
          Value="{DynamicResource {x:Static SystemColors.HighlightBrushKey}}" />  
  
        <!-- Sets the glass opacity to 1, therefore, the   
             glass "appears" when user mouses over it. -->  
        <Setter Property="Rectangle.Opacity" Value="1" TargetName="glassCube" />  
  
        <!-- Makes the text slightly blurry as though you   
             were looking at it through blurry glass. -->  
        <Setter Property="ContentPresenter.BitmapEffect"   
          TargetName="myContentPresenter">  
          <Setter.Value>  
            <BlurBitmapEffect Radius="1" />  
          </Setter.Value>  
        </Setter>  
      </Trigger>  
  
    <ControlTemplate.Triggers/>  
    ```  
  
     Appuyez sur F5 pour exécuter l'application et visionner l'effet quand vous passez le pointeur de la souris sur les boutons.  
  
3.  **Ajouter un déclencheur de focus :** nous allons maintenant ajouter des accesseurs Set semblables pour gérer le cas où le focus est sur le bouton \(par exemple, après que l'utilisateur clique dessus\).  
  
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
      <!-- Set properties when button has focus. -->  
      <Trigger Property="IsFocused" Value="true">  
        <Setter Property="Rectangle.Opacity" Value="1"       TargetName="glassCube" />  
        <Setter Property="Rectangle.Stroke" TargetName="outerRectangle"  
          Value="{DynamicResource {x:Static SystemColors.HighlightBrushKey}}" />  
        <Setter Property="Rectangle.Opacity" Value="1" TargetName="glassCube" />  
      </Trigger>  
  
    </ControlTemplate.Triggers>  
    ```  
  
     Appuyez sur F5 pour exécuter l'application et cliquez sur l'un des boutons.  Remarquez que les boutons restent en surbrillance après avoir cliqué dessus car il a encore le focus.  Si vous cliquez sur un autre bouton, le nouveau bouton gagne le focus pendant que le dernier le perd.  
  
4.  **Ajouter des animations pour**  <xref:System.Windows.UIElement.MouseEnter> **et** <xref:System.Windows.UIElement.MouseLeave> **:** nous allons maintenant ajouter quelques animations aux déclencheurs.  Ajoutez la balise suivante n'importe où dans le bloc `ControlTemplate.Triggers`.  
  
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
  
     Le rectangle de verre se réduit lorsque le pointeur de la souris passe sur le bouton et revient à sa taille normale lorsque le pointeur repart.  
  
     Deux animations se déclenchent lorsque le pointeur va sur le bouton \(l'événement <xref:System.Windows.UIElement.MouseEnter> est déclenché\).  Ces animations réduisent le rectangle de verre le long des axes X et Y.  Notez les propriétés sur les éléments <xref:System.Windows.Media.Animation.DoubleAnimation> — <xref:System.Windows.Media.Animation.Timeline.Duration%2A> et <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>.  L'<xref:System.Windows.Media.Animation.Timeline.Duration%2A> spécifie que l'animation a lieu pendant une demi\-seconde, et <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> spécifie que le verre se réduit de 10 %.  
  
     Le deuxième déclencheur d'événements \(<xref:System.Windows.UIElement.MouseLeave>\) arrête simplement le premier.  Lorsque vous arrêtez un <xref:System.Windows.Media.Animation.Storyboard>, toutes les propriétés animées retournent à leurs valeurs par défaut.  Par conséquent, lorsque l'utilisateur déplace le pointeur du bouton, le bouton retrouve l'apparence qu'il avait avant que le pointeur de la souris ne soit passé dessus.  Pour plus d'informations sur les animations, consultez [Vue d'ensemble de l'animation](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).  
  
5.  **Ajouter une animation lorsque le bouton est cliqué :** la dernière étape consiste à ajouter un déclencheur pour le cas où l'utilisateur clique sur le bouton.  Ajoutez la balise suivante n'importe où dans le bloc `ControlTemplate.Triggers` :  
  
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
  
     Appuyez sur F5 pour exécuter l'application et cliquez sur l'un des boutons.  Lorsque vous cliquez sur un bouton, le rectangle de verre tourne.  
  
## Résumé  
 Dans cette procédure pas à pas, vous avez effectué les exercices suivants :  
  
-   Ciblé un <xref:System.Windows.Style> à un type d'objet \(<xref:System.Windows.Controls.Button>\).  
  
-   Contrôlé des propriétés de base des boutons dans l'application entière à l'aide du <xref:System.Windows.Style>.  
  
-   Créé des ressources telles que des gradients à utiliser pour les valeurs de propriété des accesseurs Set <xref:System.Windows.Style>.  
  
-   Personnalisé l'apparence de boutons dans l'application entière en appliquant un modèle aux boutons.  
  
-   Personnalisé le comportement des boutons en réponse aux actions des utilisateurs \(telles que <xref:System.Windows.UIElement.MouseEnter>, <xref:System.Windows.UIElement.MouseLeave> et  <xref:System.Windows.Controls.Primitives.ButtonBase.Click>\) qui comportaient des effets d'animation.  
  
## Voir aussi  
 [Créer un bouton à l'aide de Microsoft Expression Blend](../../../../docs/framework/wpf/controls/walkthrough-create-a-button-by-using-microsoft-expression-blend.md)   
 [Application d'un style et création de modèles](../../../../docs/framework/wpf/controls/styling-and-templating.md)   
 [Vue d'ensemble de l'animation](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)   
 [Vue d'ensemble de la peinture avec des couleurs unies ou des dégradés](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)   
 [Vue d'ensemble des effets bitmap](../../../../docs/framework/wpf/graphics-multimedia/bitmap-effects-overview.md)