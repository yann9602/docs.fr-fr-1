---
title: "Propriétés de dépendance"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 212cfb1e-cec4-4047-94a6-47209b387f6f
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: b9e60f3e941dd1d7d89675f4483ae940b039ba10
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="dependency-properties"></a>Propriétés de dépendance
Une propriété de dépendance (DP) est une propriété normale qui stocke sa valeur dans une banque de propriétés au lieu de stocker dans une variable de type (champ), par exemple.  
  
 Une propriété de dépendance jointe est un type de propriété de dépendance modélisée en tant que les méthodes Get et Set statiques qui représente « propriétés », description des relations entre les objets et leurs conteneurs (par exemple, la position d’un `Button` de l’objet sur un `Panel` conteneur).  
  
 **✓ FAIRE** fournissent les propriétés de dépendance, si vous avez besoin des propriétés pour prendre en charge des fonctionnalités WPF telles que les styles, les déclencheurs, liaison de données, des animations, ressources dynamiques et d’héritage.  
  
## <a name="dependency-property-design"></a>Conception de propriété de dépendance  
 **✓ FAIRE** hériter <xref:System.Windows.DependencyObject>, ou l’un de ses sous-types, lors de l’implémentation des propriétés de dépendance. Ce type fournit une implémentation très efficace d’une banque de propriétés et prend automatiquement en charge la liaison de données WPF.  
  
 **✓ FAIRE** fournir une propriété CLR normale et un champ statique public en lecture seule le stockage d’une instance de <xref:System.Windows.DependencyProperty?displayProperty=nameWithType> pour chaque propriété de dépendance.  
  
 **✓ FAIRE** implémenter des propriétés de dépendance en appelant des méthodes d’instance <xref:System.Windows.DependencyObject.GetValue%2A?displayProperty=nameWithType> et <xref:System.Windows.DependencyObject.SetValue%2A?displayProperty=nameWithType>.  
  
 **✓ FAIRE** nom du champ de propriété de dépendance statique par suffixant le nom de la propriété « Property ».  
  
 **X ne sont pas** définir explicitement les valeurs par défaut des propriétés de dépendance dans le code ; les définir dans les métadonnées.  
  
 Si vous définissez explicitement une valeur par défaut de la propriété, vous risquez d’empêcher cette propriété soient définies par des moyens implicites, par exemple, un style.  
  
 **X ne sont pas** placez le code dans les accesseurs de propriété autre que le code standard pour accéder au champ statique.  
  
 Que code ne sera pas s’exécuter si la propriété est définie par des moyens implicites, par exemple, un style, étant donné que les styles d’utilise directement le champ statique.  
  
 **X ne sont pas** utilise les propriétés de dépendance pour stocker des données sécurisées. Propriétés de dépendance même privée est accessible publiquement.  
  
## <a name="attached-dependency-property-design"></a>Conception de propriété de dépendance jointe  
 Propriétés de dépendance décrites dans la section précédente représentent les propriétés intrinsèques du type déclarant ; par exemple, le `Text` propriété est une propriété de `TextButton`, qui le déclare. Un type spécial de propriété de dépendance est la propriété de dépendance jointe.  
  
 Un exemple classique d’une propriété jointe est le <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> propriété. La propriété représente la position de colonne pas de (la grille) du bouton, mais elle s’applique uniquement si le bouton est contenu dans une grille, et par conséquent, il est « attaché » aux boutons de grilles.  
  
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
  
 La définition d’une propriété jointe ressemble principalement similaire à celle d’une propriété de dépendance standard, à ceci près que les accesseurs sont représentées par les méthodes Get et Set statiques :  
  
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
  
## <a name="dependency-property-validation"></a>Validation de propriété de dépendance  
 Propriétés implémentent souvent ce que l'on appelle la validation. La logique de validation s’exécute lorsqu’une tentative est faite pour modifier la valeur d’une propriété.  
  
 Malheureusement, les accesseurs de propriété de dépendance ne peut pas contenir de code de validation arbitraire. Au lieu de cela, logique de validation de propriété de dépendance doit être spécifié au cours de l’inscription de la propriété.  
  
 **X ne sont pas** placer la logique de validation de propriété de dépendance dans les accesseurs de la propriété. Au lieu de cela, passez un rappel de validation à `DependencyProperty.Register` (méthode).  
  
## <a name="dependency-property-change-notifications"></a>Notifications de modification de propriété de dépendance  
 **X ne sont pas** implémenter la logique de notification de modification dans les accesseurs de propriété de dépendance. Propriétés de dépendance ont une fonctionnalité de notifications de modification intégrée qui doit être utilisée, vous devez fournir un rappel de notification de modification pour le <xref:System.Windows.PropertyMetadata>.  
  
## <a name="dependency-property-value-coercion"></a>Contrainte de valeur de propriété de dépendance  
 La contrainte de propriété a lieu lorsque la valeur donnée à un accesseur Set de propriété est modifiée par la méthode setter avant que la banque de propriétés est réellement modifiée.  
  
 **X ne sont pas** implémenter la logique de la contrainte dans les accesseurs de propriété de dépendance.  
  
 Propriétés de dépendance ont une fonctionnalité intégrée de la contrainte, et il peut être utilisé, vous devez fournir un rappel de la contrainte à la `PropertyMetadata`.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*  
  
 *Réimprimées avec l’autorisation de Pearson éducation, Inc. à partir de [règles de conception d’infrastructure : Conventions, idiomes et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série de développement Microsoft Windows.*  
  
## <a name="see-also"></a>Voir aussi  
 [Règles de conception de .NET Framework](../../../docs/standard/design-guidelines/index.md)  
 [Modèles de design courants](../../../docs/standard/design-guidelines/common-design-patterns.md)
