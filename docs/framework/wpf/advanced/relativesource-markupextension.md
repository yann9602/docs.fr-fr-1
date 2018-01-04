---
title: RelativeSource, extension de balisage
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: RelativeSource
helpviewer_keywords:
- RelativeSource markup extensions [WPF]
- XAML [WPF], RelativeSource markup extension
ms.assetid: 26be4721-49b5-4717-a92e-7d54ad0d3a81
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6ea5d269c3d455a4fbe3a34dca4335e0d8999d80
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="relativesource-markupextension"></a>RelativeSource, extension de balisage
Spécifie les propriétés d’un <xref:System.Windows.Data.RelativeSource> source de liaison, à utiliser dans un [Extension de balisage de liaison](../../../../docs/framework/wpf/advanced/binding-markup-extension.md), ou lors de la définition la <xref:System.Windows.Data.Binding.RelativeSource%2A> propriété d’un <xref:System.Windows.Data.Binding> élément établie en XAML.  
  
## <a name="xaml-attribute-usage"></a>Utilisation d'attributs XAML  
  
```xml  
<Binding RelativeSource="{RelativeSource modeEnumValue}" .../>  
```  
  
## <a name="xaml-attribute-usage-nested-within-binding-extension"></a>Utilisation des attributs XAML (imbriqués dans l'extension de liaison)  
  
```xml  
<object property="{Binding RelativeSource={RelativeSource modeEnumValue} ...}" .../>  
```  
  
## <a name="xaml-object-element-usage"></a>Utilisation d'éléments objet XAML  
  
```xml  
<Binding>  
  <Binding.RelativeSource>  
    <RelativeSource Mode="modeEnumValue"/>  
  </Binding.RelativeSource>  
</Binding>  
- or   
<Binding>  
  <Binding.RelativeSource>  
    <RelativeSource  
      Mode="FindAncestor"  
      AncestorType="{x:Type typeName}"  
      AncestorLevel="intLevel"  
    />  
  </Binding.RelativeSource>  
</Binding>  
```  
  
## <a name="xaml-values"></a>Valeurs XAML  
  
|||  
|-|-|  
|`modeEnumValue`|Une des valeurs suivantes :<br /><br /> -Le jeton de chaîne `Self`; correspond à un <xref:System.Windows.Data.RelativeSource> comme créé avec sa <xref:System.Windows.Data.RelativeSource.Mode%2A> propriété <xref:System.Windows.Data.RelativeSourceMode.Self>.<br />-Le jeton de chaîne `TemplatedParent`; correspond à un <xref:System.Windows.Data.RelativeSource> comme créé avec sa <xref:System.Windows.Data.RelativeSource.Mode%2A> propriété <xref:System.Windows.Data.RelativeSourceMode.TemplatedParent>.<br />-Le jeton de chaîne `PreviousData`; correspond à un <xref:System.Windows.Data.RelativeSource> comme créé avec sa <xref:System.Windows.Data.RelativeSource.Mode%2A> propriété <xref:System.Windows.Data.RelativeSourceMode.PreviousData>.<br />-Voir ci-dessous pour plus d’informations sur `FindAncestor` mode.|  
|`FindAncestor`|Le jeton de chaîne `FindAncestor`. L'utilisation de ce jeton accède à un mode dans lequel un `RelativeSource` spécifie un type d'ancêtre et, en option, un niveau d'ancêtre. Ce correspond à un <xref:System.Windows.Data.RelativeSource> comme créé avec sa propriété <xref:System.Windows.Data.RelativeSource.Mode%2A> définie à <xref:System.Windows.Data.RelativeSourceMode.FindAncestor>.|  
|`typeName`|Nécessaire pour le mode `FindAncestor`. Le nom d'un type, qui remplit la propriété <xref:System.Windows.Data.RelativeSource.AncestorType%2A>.|  
|`intLevel`|Facultatif pour le mode `FindAncestor`. Un niveau d'ancêtre (évalué vers la direction du parent dans l'arborescence logique).|  
  
## <a name="remarks"></a>Notes  
 `{RelativeSource TemplatedParent}`utilisations de liaison sont une technique principale qui traite un concept de séparation de l’interface utilisateur d’un contrôle et la logique d’un contrôle. Cela permet la liaison à partir de la définition de modèle au parent basé sur des modèles (instance de l'objet à l'exécution où le modèle est appliqué). Dans ce cas, le [Extension de balisage TemplateBinding](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md) est en fait un raccourci pour l’expression de liaison suivante : `{Binding RelativeSource={RelativeSource TemplatedParent}}`. `TemplateBinding`ou `{RelativeSource TemplatedParent}` utilisations sont uniquement pertinentes dans le code XAML qui définit un modèle. Pour plus d’informations, consultez [Extension de balisage TemplateBinding](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md)  
  
 `{RelativeSource FindAncestor}`est principalement utilisée dans les modèles de contrôle ou compositions de l’interface utilisateur autonomes prévisibles, pour les cas où un contrôle est toujours censé être dans une arborescence d’éléments visuels d’un certain type ancêtre. Par exemple, les éléments d'un contrôle d'éléments peuvent utiliser des utilisations de `FindAncestor` pour les lier aux propriétés de leur ancêtre parent du contrôle d'éléments. Ou les éléments qui font partie de la composition de contrôle dans un modèle peuvent utiliser des liaisons de `FindAncestor` aux éléments parents dans cette même structure de composition.  
  
 Dans la syntaxe d'élément objet du mode `FindAncestor` indiqué dans les sections de syntaxe XAML, la deuxième syntaxe d'élément objet est utilisée spécifiquement pour le mode `FindAncestor`. Le mode `FindAncestor` requiert une valeur <xref:System.Windows.Data.RelativeSource.AncestorType%2A>. Vous devez définir <xref:System.Windows.Data.RelativeSource.AncestorType%2A> comme un attribut à l’aide un [x : Type, Extension de balisage](../../../../docs/framework/xaml-services/x-type-markup-extension.md) référence au type d’ancêtre à rechercher. La valeur <xref:System.Windows.Data.RelativeSource.AncestorType%2A> est utilisée lorsque la demande de liaison est traitée lors de l'exécution.  
  
 Pour le mode `FindAncestor`, la propriété <xref:System.Windows.Data.RelativeSource.AncestorLevel%2A> facultative peut contribuer à désambiguïser la recherche d'ancêtre dans les cas où il existe peut-être plusieurs ancêtres de ce type présents dans l'arborescence d'éléments.  
  
 Pour plus d'informations sur l'utilisation du mode `FindAncestor`, consultez <xref:System.Windows.Data.RelativeSource>.  
  
 `{RelativeSource Self}`est utile pour les scénarios où une seule propriété d’une instance doit s’appuyer sur la valeur d’une autre propriété de la même instance et aucune relation de propriété de dépendance général (par exemple, la contrainte) déjà existe entre ces deux propriétés. Bien qu’il soit rare que deux propriétés existent sur un objet, telles que les valeurs sont littéralement identiques (et sont identiquement typées), vous pouvez également appliquer un `Converter` paramètre à une liaison qui a `{RelativeSource Self}`et utiliser le convertisseur pour convertir entre source et types de cibles. Un autre scénario de `{RelativeSource Self}` en tant qu’un <xref:System.Windows.MultiDataTrigger>.  
  
 Par exemple, le code XAML suivant définit un élément <xref:System.Windows.Shapes.Rectangle> tels que tout ce que la valeur est entrée pour <xref:System.Windows.FrameworkElement.Width%2A>, <xref:System.Windows.Shapes.Rectangle> est toujours angle droit : `<Rectangle Width="200" Height="{Binding RelativeSource={RelativeSource Self}, Path=Width}" .../>`  
  
 `{RelativeSource PreviousData}`est utile dans les modèles de données, ou dans les cas où les liaisons utilisent une collection comme source de données. Vous pouvez utiliser `{RelativeSource PreviousData}` pour mettre en surbrillance les relations entre les éléments de données adjacents de la collection. Une technique connexe est de générer <xref:System.Windows.Data.MultiBinding> entre des éléments actuels et précédents dans la source de données, et d'utiliser un convertisseur sur cette liaison pour déterminer la différence entre les deux éléments et leurs propriétés.  
  
 Dans l'exemple suivant, le premier <xref:System.Windows.Controls.TextBlock> dans le modèle d'éléments affiche le numéro actuel. La seconde <xref:System.Windows.Controls.TextBlock> liaison est un <xref:System.Windows.Data.MultiBinding> qui a nominalement deux <xref:System.Windows.Data.Binding> constituants : l’enregistrement en cours et une liaison qui utilise délibérément l’enregistrement de données précédent à l’aide de `{RelativeSource PreviousData}`. Ensuite, un convertisseur sur <xref:System.Windows.Data.MultiBinding> calcule la différence et la retourne à la liaison.  
  
```xml  
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
  
 Description de la liaison de données comme un concept n’est pas couverte ici, consultez [vue d’ensemble de la liaison de données](../../../../docs/framework/wpf/data/data-binding-overview.md).  
  
 Dans le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] implémentation du processeur XAML, la gestion de cette extension de balisage est définie par le <xref:System.Windows.Data.RelativeSource> classe.  
  
 `RelativeSource` est une extension de balisage. Les extensions de balisage sont généralement implémentées pour éviter que les valeurs d’attribut ne soient autre chose que des valeurs littérales ou des noms de gestionnaire et lorsque l’exigence dépasse le cadre de la définition de convertisseurs de type sur certains types ou propriétés. Toutes les extensions de balisage en cours d’utilisation XAML le `{` et `}` caractères dans leur syntaxe d’attribut, qui est la convention selon laquelle un processeur XAML reconnaît qu’une extension de balisage doit traiter l’attribut. Pour plus d’informations, consultez [Extensions de balisage et XAML WPF](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Data.Binding>  
 [Application d’un style et création de modèles](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [Vue d’ensemble du langage XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [Extensions de balisage et XAML WPF](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)  
 [Vue d’ensemble de la liaison de données](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Vue d'ensemble des déclarations de liaison](../../../../docs/framework/wpf/data/binding-declarations-overview.md)  
 [x:Type, extension de balisage](../../../../docs/framework/xaml-services/x-type-markup-extension.md)
