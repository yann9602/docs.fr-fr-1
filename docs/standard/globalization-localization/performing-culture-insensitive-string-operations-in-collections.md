---
title: "Exécution d’opérations de chaînes indépendantes de la culture dans des collections"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CaseInsensitiveComparer class, using
- CollectionsUtil.CreateCaseInsensitiveHashtable method
- culture-insensitive string operations, collections
- collections [.NET Framework], culture-insensitive string operations
- CaseInsensitiveHashCodeProvider class, using
- ArrayList.Sort method
- SortedList class, culture-insensitive string operations
- culture parameter
ms.assetid: 5cdc9396-a64b-4615-a1cd-b605db4c5983
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a1ecba9c055f8e99d26283c7f37c2430dc17bf31
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="performing-culture-insensitive-string-operations-in-collections"></a>Exécution d’opérations de chaînes indépendantes de la culture dans des collections
Contient des classes et membres dans le <xref:System.Collections> espace de noms qui fournissent un comportement dépendant de la culture par défaut. Les constructeurs par défaut pour le <xref:System.Collections.CaseInsensitiveComparer> et <xref:System.Collections.CaseInsensitiveHashCodeProvider> classes initialiser une nouvelle instance en utilisant la <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> propriété. Toutes les surcharges de la <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType> méthode crée une nouvelle instance de la <xref:System.Collections.Hashtable> à l’aide de la classe le `Thread.CurrentCulture` propriété par défaut. Les surcharges de la <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType> méthode effectuer des tris dépendante de la culture par défaut à l’aide `Thread.CurrentCulture`. Tri et la recherche dans un <xref:System.Collections.SortedList> peuvent être affectés par `Thread.CurrentCulture` lorsque les chaînes sont utilisées comme clés. Suivez les recommandations d’utilisation fournies dans cette section pour obtenir des résultats indépendants de la culture à partir de ces classes et méthodes dans l’espace de noms `Collections`.  
  
 **Remarque** passage <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> pour une comparaison de méthode effectue une comparaison indépendante de la culture. Toutefois, elle n’entraîne pas une comparaison non linguistique, par exemple, pour les chemins d’accès de fichier, les clés de Registre et les variables d’environnement. Elle ne prend pas non plus en charge les décisions de sécurité basées sur le résultat de la comparaison. Pour une comparaison non linguistique ou la prise en charge pour les décisions de sécurité basée sur les résultats, l’application doit utiliser une méthode de comparaison qui accepte une <xref:System.StringComparison> valeur. L’application doit ensuite passer <xref:System.StringComparison>.  
  
## <a name="using-the-caseinsensitivecomparer-and-caseinsensitivehashcodeprovider-classes"></a>Utilisation des classes CaseInsensitiveComparer et CaseInsensitiveHashCodeProvider  
 Les constructeurs par défaut pour `CaseInsensitiveHashCodeProvider` et `CaseInsensitiveComparer` lancent une nouvelle instance de la classe à l’aide de `Thread.CurrentCulture`, qui entraîne un comportement dépendant de la culture. L’exemple de code suivant montre le constructeur pour un `Hashtable` qui est dépendant de la culture car il utilise les constructeurs par défaut pour `CaseInsensitiveHashCodeProvider` et `CaseInsensitiveComparer`.  
  
```vb  
internalHashtable = New Hashtable(CaseInsensitiveHashCodeProvider.Default, CaseInsensitiveComparer.Default)  
```  
  
```csharp  
internalHashtable = new Hashtable(CaseInsensitiveHashCodeProvider.Default, CaseInsensitiveComparer.Default);  
```  
  
 Si vous souhaitez créer la culture `Hashtable` à l’aide de la `CaseInsensitiveComparer` et `CaseInsensitiveHashCodeProvider` classes, initialisez les nouvelles instances de ces classes à l’aide des constructeurs qui acceptent un `culture` paramètre. Pour le paramètre `culture`, spécifiez <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>. L’exemple de code suivant montre le constructeur pour un `Hashtable` indépendant de la culture.  
  
```vb  
internalHashtable = New Hashtable(New  
    CaseInsensitiveHashCodeProvider(CultureInfo.InvariantCulture),  
    New CaseInsensitiveComparer(CultureInfo.InvariantCulture))  
```  
  
```csharp  
internalHashtable = new Hashtable(new CaseInsensitiveHashCodeProvider  
    (CultureInfo.InvariantCulture),   
    new CaseInsensitiveComparer(CultureInfo.InvariantCulture));  
```  
  
## <a name="using-the-collectionsutilcreatecaseinsensitivehashtable-method"></a>Utilisation de la méthode CollectionsUtil.CreateCaseInsensitiveHashtable  
 La méthode `CollectionsUtil.CreateCaseInsensitiveHashTable` est un raccourci utile pour créer une nouvelle instance de la classe `Hashtable` qui ignore la casse des chaînes. Toutefois, toutes les surcharges de la méthode `CollectionsUtil.CreateCaseInsensitiveHashTable` sont dépendantes de la culture car elles utilisent la propriété `Thread.CurrentCulture`. Vous ne pouvez pas créer un `Hashtable` indépendant de la culture à l’aide de cette méthode. Pour créer un `Hashtable` indépendant de la culture, utilisez le constructeur `Hashtable` qui accepte un paramètre `culture`. Pour le paramètre `culture`, spécifiez `CultureInfo.InvariantCulture`. L’exemple de code suivant montre le constructeur pour un `Hashtable` indépendant de la culture.  
  
```vb  
internalHashtable = New Hashtable(New  
    CaseInsensitiveHashCodeProvider(CultureInfo.InvariantCulture),  
    New CaseInsensitiveComparer(CultureInfo.InvariantCulture))  
```  
  
```csharp  
internalHashtable = new Hashtable(new CaseInsensitiveHashCodeProvider  
    (CultureInfo.InvariantCulture),   
    new CaseInsensitiveComparer(CultureInfo.InvariantCulture));  
```  
  
<a name="cpconperformingculture-insensitivestringoperationsincollectionsanchor1"></a>   
## <a name="using-the-sortedlist-class"></a>Utilisation de la classe SortedList  
 Un `SortedList` représente une collection de paires clé/valeur triées par les clés et accessibles par clé et par index. Lorsque vous utilisez un `SortedList` où des chaînes sont les clés, le tri et la recherche peuvent être affectés par la propriété `Thread.CurrentCulture`. Pour obtenir un comportement indépendant de la culture d’un `SortedList`, créez un `SortedList` à l’aide d’un des constructeurs qui acceptent un paramètre `comparer`. Le `comparer` paramètre spécifie le <xref:System.Collections.IComparer> implémentation à utiliser lors de la comparaison de clés. Pour le paramètre, spécifiez une classe de comparateur personnalisée qui utilise `CultureInfo.InvariantCulture` pour comparer des clés. L’exemple suivant illustre une classe de comparateur indépendante de la culture personnalisée que vous pouvez spécifier en tant que paramètre `comparer` dans un constructeur `SortedList`.  
  
```vb  
Imports System  
Imports System.Collections  
Imports System.Globalization  
  
Friend Class InvariantComparer  
    Implements IComparer   
    Private m_compareInfo As CompareInfo  
    Friend Shared [Default] As New InvariantComparer()  
  
    Friend Sub New()  
        m_compareInfo = CultureInfo.InvariantCulture.CompareInfo  
    End Sub     
  
    Public Function Compare(a As Object, b As Object) As Integer _  
            Implements IComparer.Compare  
        Dim sa As String = CType(a, String)  
        Dim sb As String = CType(b, String)  
        If Not (sa Is Nothing) And Not (sb Is Nothing) Then  
            Return m_compareInfo.Compare(sa, sb)  
        Else  
            Return Comparer.Default.Compare(a, b)  
        End If  
    End Function  
End Class  
```  
  
```csharp  
using System;  
using System.Collections;  
using System.Globalization;  
  
internal class InvariantComparer : IComparer   
{  
    private CompareInfo m_compareInfo;  
    internal static readonly InvariantComparer Default = new  
        InvariantComparer();  
  
    internal InvariantComparer()   
    {  
        m_compareInfo = CultureInfo.InvariantCulture.CompareInfo;  
    }  
  
    public int Compare(Object a, Object b)  
    {  
        String sa = a as String;  
        String sb = b as String;  
        if (sa != null && sb != null)  
            return m_compareInfo.Compare(sa, sb);  
        else  
            return Comparer.Default.Compare(a,b);  
    }  
}  
```  
  
 En général, si vous utilisez un `SortedList` sur des chaînes sans spécifier de comparateur indifférent personnalisé, une modification sur `Thread.CurrentCulture` lorsque la liste est remplie peut invalider cette liste.  
  
## <a name="using-the-arraylistsort-method"></a>Utilisation de la méthode ArrayList.Sort  
 Les surcharges de la méthode `ArrayList.Sort` effectuent des tris dépendants de la culture par défaut à l’aide de la propriété `Thread.CurrentCulture`. Les résultats peuvent varier selon la culture en raison des différents ordres de tri. Pour supprimer un comportement dépendant de la culture, utilisez les surcharges de cette méthode qui acceptent une implémentation `IComparer`. Pour le paramètre `comparer`, spécifiez une classe de comparateur indifférent personnalisée qui utilise `CultureInfo.InvariantCulture`. Un exemple de classe de comparateur indifférent personnalisée est fourni dans la rubrique [Utilisation de la classe SortedList](#cpconperformingculture-insensitivestringoperationsincollectionsanchor1).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Collections.CaseInsensitiveComparer>  
 <xref:System.Collections.CaseInsensitiveHashCodeProvider>  
 <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType>  
 <xref:System.Collections.SortedList>  
 <xref:System.Collections.Hashtable>  
 <xref:System.Collections.IComparer>  
 [Exécution d'opérations de chaînes indépendantes de la culture](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)  
 <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType>
