---
title: "Propri&#233;t&#233;s de d&#233;pendance | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
ms.assetid: 212cfb1e-cec4-4047-94a6-47209b387f6f
caps.latest.revision: 4
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 4
---
# Propri&#233;t&#233;s de d&#233;pendance
Une propriété de dépendance \(DP\) est une propriété normale qui stocke sa valeur dans une banque de propriétés au lieu de stocker dans une variable de type \(champ\), par exemple.  
  
 Une propriété de dépendance attachée est un type de propriété de dépendance modélisée en tant que les méthodes Get et Set statiques qui représente « propriétés » qui décrit les relations entre les objets et leurs conteneurs \(par exemple, la position d’un `Button` de l’objet sur un `Panel` conteneur\).  
  
 **✓ faire** les propriétés de dépendance, vous fournir les propriétés pour prendre en charge des fonctionnalités WPF telles que les styles, déclencheurs, liaison de données, des animations, ressources dynamiques et l’héritage.  
  
## Conception des propriétés de dépendance  
 **✓ faire** héritent <xref:System.Windows.DependencyObject>, ou l’un de ses sous\-types, lors de l’implémentation des propriétés de dépendance. Ce type fournit une implémentation très efficace d’une banque de propriétés et prend automatiquement en charge la liaison de données WPF.  
  
 **✓ faire** fournir une propriété CLR normale et un champ statique public en lecture seule le stockage d’une instance de <xref:System.Windows.DependencyProperty?displayProperty=fullName> pour chaque propriété de dépendance.  
  
 **✓ faire** implémenter des propriétés de dépendance en appelant des méthodes d’instance <xref:System.Windows.DependencyObject.GetValue%2A?displayProperty=fullName> et <xref:System.Windows.DependencyObject.SetValue%2A?displayProperty=fullName>.  
  
 **✓ faire** nom de champ statique de la propriété de dépendance en suffixant le nom de la propriété « Property ».  
  
 **X ne pas** définir explicitement les valeurs par défaut des propriétés de dépendance dans le code ; les définir dans les métadonnées.  
  
 Si vous définissez explicitement une valeur par défaut de la propriété, vous pouvez empêcher cette propriété soient définies par des moyens implicites, par exemple un style.  
  
 **X ne pas** placer le code dans les accesseurs de propriété autre que le code standard pour accéder au champ statique.  
  
 Que code n’exécutera si la propriété est définie par des moyens implicites, par exemple, un style, étant donné que les styles d’utilise directement le champ statique.  
  
 **X ne pas** utilise les propriétés de dépendance pour stocker des données sécurisées. Propriétés de dépendance même privées sont accessibles publiquement.  
  
## Conception des propriétés de dépendance attachée  
 Propriétés de dépendance décrites dans la section précédente représentent les propriétés intrinsèques du type déclarant ; par exemple, le `Text` constitue une propriété de `TextButton`, qui le déclare. Un type spécial de propriété de dépendance est la propriété de dépendance attachée.  
  
 Un exemple classique d’une propriété jointe est le <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=fullName> propriété. La propriété représente la position de colonne \(pas de la grille\) du bouton, mais elle n’est utile que si le bouton est contenu dans une grille, et par conséquent il est « associé » à boutons par grilles.  
  
```  
<Grid>  
    <Grid.ColumnDefinitions>  
        <ColumnDefinition />  
        <ColumnDefinition />  
    </Grid.ColumnDefinitions>  
  
    <Button Grid.Column="0">Click</Button>  
    <Button Grid.Column="1">Clack</Button>  
</Grid>  
```  
  
 La définition d’une propriété jointe ressemble essentiellement similaire à celui d’une propriété de dépendance standard, à ceci près que les accesseurs sont représentés par les méthodes Get et Set statiques :  
  
```  
public class Grid {  
  
    public static int GetColumn(DependencyObject obj) {  
        return (int)obj.GetValue(ColumnProperty);  
    }  
  
    public static void SetColumn(DependencyObject obj, int value) {  
        obj.SetValue(ColumnProperty,value);  
    }  
  
    public static readonly DependencyProperty ColumnProperty =  
        DependencyProperty.RegisterAttached(  
            "Column",  
            typeof(int),  
            typeof(Grid)  
    );  
}  
```  
  
## Validation de propriété de dépendance  
 Propriétés implémentent souvent ce que l'on appelle la validation. La logique de validation s’exécute lorsqu’une tentative est faite pour modifier la valeur d’une propriété.  
  
 Malheureusement, les accesseurs de propriété de dépendance ne peut pas contenir le code de validation arbitraire. Au lieu de cela, logique de validation de propriété de dépendance doit être spécifié lors de l’inscription de propriété.  
  
 **X ne pas** placer la logique de validation de propriété de dépendance dans les accesseurs de la propriété. Au lieu de cela, passez un rappel de validation pour `DependencyProperty.Register` \(méthode\).  
  
## Notifications de modification de propriété de dépendance  
 **X ne pas** implémenter la logique de notification de modification dans les accesseurs de propriété de dépendance. Propriétés de dépendance intègrent une fonction de notifications de modification intégrée qui doit être utilisée en fournissant un rappel de notification de modification pour le <xref:System.Windows.PropertyMetadata>.  
  
## Contrainte de valeur de propriété de dépendance  
 Contrainte de propriété se produit lorsque la valeur donnée à un accesseur Set de propriété est modifiée par la méthode setter avant que la banque de propriétés est en fait modifiée.  
  
 **X ne pas** implémenter la logique de la contrainte dans les accesseurs de propriété de dépendance.  
  
 Propriétés de dépendance ont une fonctionnalité intégrée de contrainte, et il peut être utilisé en fournissant un rappel de contrainte à la `PropertyMetadata`.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*  
  
 *Réimprimé avec l’autorisation de Pearson éducation, Inc. à partir de [Framework Design Guidelines : Conventions, langages et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison\-Wesley Professional dans le cadre de la série de développement de Microsoft Windows.*  
  
## Voir aussi  
 [Instructions de conception d’infrastructure](../../../docs/standard/design-guidelines/index.md)   
 [Modèles de conception courants](../../../docs/standard/design-guidelines/common-design-patterns.md)