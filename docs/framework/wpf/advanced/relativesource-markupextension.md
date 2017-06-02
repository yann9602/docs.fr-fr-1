---
title: "RelativeSource, extension de balisage | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "RelativeSource"
helpviewer_keywords: 
  - "RelativeSource (extensions de balisage)"
  - "XAML, RelativeSource (extension de balisage)"
ms.assetid: 26be4721-49b5-4717-a92e-7d54ad0d3a81
caps.latest.revision: 18
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 18
---
# RelativeSource, extension de balisage
Spécifie les propriétés d'une source de liaison <xref:System.Windows.Data.RelativeSource>, à utiliser dans un [Binding, extension de balisage](../../../../docs/framework/wpf/advanced/binding-markup-extension.md), ou lors de la définition de la propriété <xref:System.Windows.Data.Binding.RelativeSource%2A> d'un élément <xref:System.Windows.Data.Binding> établie dans XAML.  
  
## Utilisation d'attributs XAML  
  
```  
<Binding RelativeSource="{RelativeSource modeEnumValue}" .../>  
```  
  
## Utilisation des attributs XAML \(imbriqués dans l'extension de liaison\)  
  
```  
<object property="{Binding RelativeSource={RelativeSource modeEnumValue} ...}" .../>  
```  
  
## Utilisation d'éléments objet XAML  
  
```  
<Binding>  
  <Binding.RelativeSource>  
    <RelativeSource Mode="modeEnumValue"/>  
  </Binding.RelativeSource>  
</Binding>  
- or   
<Binding>  
  <Binding.RelativeSource>  
    <RelativeSource  
      Mode="FindAncestor"  
      AncestorType="{x:Type typeName}"  
      AncestorLevel="intLevel"  
    />  
  </Binding.RelativeSource>  
</Binding>  
```  
  
## Valeurs XAML  
  
|||  
|-|-|  
|`modeEnumValue`|Une des valeurs suivantes :<br /><br /> -   Le jeton de chaîne `Self` correspond à un <xref:System.Windows.Data.RelativeSource> comme créé avec sa propriété <xref:System.Windows.Data.RelativeSource.Mode%2A> définie à <xref:System.Windows.Data.RelativeSourceMode>.<br />-   Le jeton de chaîne `TemplatedParent` correspond à un <xref:System.Windows.Data.RelativeSource> comme créé avec sa propriété <xref:System.Windows.Data.RelativeSource.Mode%2A> définie à <xref:System.Windows.Data.RelativeSourceMode>.<br />-   Le jeton de chaîne `PreviousData` correspond à un <xref:System.Windows.Data.RelativeSource> comme créé avec sa propriété <xref:System.Windows.Data.RelativeSource.Mode%2A> définie à <xref:System.Windows.Data.RelativeSourceMode>.<br />-   Voir ci\-dessous pour des informations sur le mode `FindAncestor`.|  
|`FindAncestor`|Le jeton de chaîne `FindAncestor`.  L'utilisation de ce jeton accède à un mode dans lequel un `RelativeSource` spécifie un type d'ancêtre et, en option, un niveau d'ancêtre.  Ce correspond à un <xref:System.Windows.Data.RelativeSource> comme créé avec sa propriété <xref:System.Windows.Data.RelativeSource.Mode%2A> définie à <xref:System.Windows.Data.RelativeSourceMode>.|  
|`typeName`|Nécessaire pour le mode `FindAncestor`.  Le nom d'un type, qui remplit la propriété <xref:System.Windows.Data.RelativeSource.AncestorType%2A>.|  
|`intLevel`|Facultatif pour le mode `FindAncestor`.  Un niveau d'ancêtre \(évalué vers la direction du parent dans l'arborescence logique\).|  
  
## Notes  
 Les utilisations de liaison de `{RelativeSource TemplatedParent}` sont une technique principale qui gère un concept plus vaste de séparation de l'interface utilisateur d'un contrôle et d'une logique de contrôle.  Cela permet la liaison à partir de la définition de modèle au parent basé sur des modèles \(instance de l'objet à l'exécution où le modèle est appliqué\).  Dans ce cas, [TemplateBinding, extension de balisage](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md) est en fait un raccourci pour l'expression de liaison suivante : `{Binding RelativeSource={RelativeSource TemplatedParent}}`.  Les utilisations de `TemplateBinding` ou de `{RelativeSource TemplatedParent}` sont tous deux uniquement pertinents dans le code XAML qui définit un modèle.  Pour plus d'informations, consultez [TemplateBinding, extension de balisage](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md).  
  
 `{RelativeSource FindAncestor}` est principalement utilisé dans les modèles de contrôle ou compositions autonomes prédictibles lors de l'interface utilisateur, dans les cas où un contrôle est toujours supposé être dans une arborescence d'éléments visuels d'un certain type ancêtre.  Par exemple, les éléments d'un contrôle d'éléments peuvent utiliser des utilisations de `FindAncestor` pour les lier aux propriétés de leur ancêtre parent du contrôle d'éléments.  Ou les éléments qui font partie de la composition de contrôle dans un modèle peuvent utiliser des liaisons de `FindAncestor` aux éléments parents dans cette même structure de composition.  
  
 Dans la syntaxe d'élément objet du mode `FindAncestor` indiqué dans les sections de syntaxe XAML, la deuxième syntaxe d'élément objet est utilisée spécifiquement pour le mode `FindAncestor`.  Le mode `FindAncestor` requiert une valeur <xref:System.Windows.Data.RelativeSource.AncestorType%2A>.  Vous devez affecter <xref:System.Windows.Data.RelativeSource.AncestorType%2A> comme un attribut à l'aide d'une référence [x:Type, extension de balisage](../../../../docs/framework/xaml-services/x-type-markup-extension.md) au type d'ancêtre à rechercher.  La valeur <xref:System.Windows.Data.RelativeSource.AncestorType%2A> est utilisée lorsque la demande de liaison est traitée lors de l'exécution.  
  
 Pour le mode `FindAncestor`, la propriété <xref:System.Windows.Data.RelativeSource.AncestorLevel%2A> facultative peut contribuer à désambiguïser la recherche d'ancêtre dans les cas où il existe peut\-être plusieurs ancêtres de ce type présents dans l'arborescence d'éléments.  
  
 Pour plus d'informations sur l'utilisation du mode `FindAncestor`, consultez <xref:System.Windows.Data.RelativeSource>.  
  
 `{RelativeSource Self}` est utile pour les scénarios où une propriété d'instance doit dépendre de la valeur d'une autre propriété de la même instance et aucune relation générale des propriétés de dépendance \(telle que la contrainte\) n'existe déjà entre ces deux propriétés.  Bien qu'il soit rare que deux propriétés existent sur un objet de telle façon que les valeurs sont littéralement identiques \(et sont identiquement typées\), vous pouvez également appliquer un paramètre `Converter` à une liaison qui a `{RelativeSource Self}` et utiliser le convertisseur pour convertir entre la source et les types cibles.  Un autre scénario pour `{RelativeSource Self}` est dans le cadre de <xref:System.Windows.MultiDataTrigger>.  
  
 Par exemple, le code XAML suivant définit un élément <xref:System.Windows.Shapes.Rectangle> tels que tout ce que la valeur est entrée pour <xref:System.Windows.FrameworkElement.Width%2A>, <xref:System.Windows.Shapes.Rectangle> est toujours angle droit : `<Rectangle Width="200" Height="{Binding RelativeSource={RelativeSource Self}, Path=Width}" .../>`  
  
 `{RelativeSource PreviousData}` est utile dans les modèles de données ou dans les cas où les liaisons utilisent une collection comme source de données.  Vous pouvez utiliser `{RelativeSource PreviousData}` pour mettre en surbrillance les relations entre les éléments de données adjacents de la collection.  Une technique connexe est de générer <xref:System.Windows.Data.MultiBinding> entre des éléments actuels et précédents dans la source de données, et d'utiliser un convertisseur sur cette liaison pour déterminer la différence entre les deux éléments et leurs propriétés.  
  
 Dans l'exemple suivant, le premier <xref:System.Windows.Controls.TextBlock> dans le modèle d'éléments affiche le numéro actuel.  La deuxième liaison de <xref:System.Windows.Controls.TextBlock> est <xref:System.Windows.Data.MultiBinding> qui a nominalement deux constituants de <xref:System.Windows.Data.Binding> : l'enregistrement courant, et une liaison qui utilise délibérément l'enregistrement de données précédent à l'aide de `{RelativeSource PreviousData}`.  Ensuite, un convertisseur sur <xref:System.Windows.Data.MultiBinding> calcule la différence et la retourne à la liaison.  
  
```  
<ListBox Name="fibolist">  
    <ListBox.ItemTemplate>  
        <DataTemplate>  
            <StackPanel Orientation="Horizontal">  
            <TextBlock Text="{Binding}"/>  
            <TextBlock>, difference = </TextBlock>  
                <TextBlock>  
                    <TextBlock.Text>  
                        <MultiBinding Converter="{StaticResource DiffConverter}">  
                            <Binding/>  
                            <Binding RelativeSource="{RelativeSource PreviousData}"/>  
                        </MultiBinding>  
                    </TextBlock.Text>  
                </TextBlock>  
            </StackPanel>  
            </DataTemplate>  
    </ListBox.ItemTemplate>  
```  
  
 La description de la liaison de données en tant que concept n'est pas couverte ici, consultez [Vue d'ensemble de la liaison de données](../../../../docs/framework/wpf/data/data-binding-overview.md).  
  
 Dans l'implémentation de processeur XAML [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], la gestion de cette extension de balisage est définie par la classe <xref:System.Windows.Data.RelativeSource>.  
  
 `RelativeSource` est une extension de balisage.  Les extensions de balisage sont généralement implémentées pour éviter que les valeurs d'attribut ne soient autre chose que des valeurs littérales ou des noms de gestionnaire et lorsque l'exigence dépasse le cadre de la définition de convertisseurs de type sur certains types ou propriétés.  En XAML, toutes les extensions de balisage utilisent les caractères `{` et `}` dans leur syntaxe d'attributs, convention selon laquelle un processeur XAML reconnaît qu'une extension de balisage doit traiter l'attribut.  Pour plus d'informations, consultez [Extensions de balisage et XAML WPF](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).  
  
## Voir aussi  
 <xref:System.Windows.Data.Binding>   
 [Application d'un style et création de modèles](../../../../docs/framework/wpf/controls/styling-and-templating.md)   
 [Vue d'ensemble du langage XAML \(WPF\)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)   
 [Extensions de balisage et XAML WPF](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)   
 [Vue d'ensemble de la liaison de données](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [Vue d'ensemble des déclarations de liaison](../../../../docs/framework/wpf/data/binding-declarations-overview.md)   
 [x:Type, extension de balisage](../../../../docs/framework/xaml-services/x-type-markup-extension.md)