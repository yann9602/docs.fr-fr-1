---
title: "Ex&#233;cution d&#39;op&#233;rations de cha&#238;nes ind&#233;pendantes de la culture dans des collections | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ArrayList.Sort (méthode)"
  - "CaseInsensitiveComparer (classe), utilisation"
  - "CaseInsensitiveHashCodeProvider (classe), utilisation"
  - "collections (.NET Framework), opérations de chaînes indépendantes de la culture"
  - "CollectionsUtil.CreateCaseInsensitiveHashtable (méthode)"
  - "culture (paramètre)"
  - "opérations de chaînes indépendantes de la culture, collections"
  - "SortedList (classe), opérations de chaînes indépendantes de la culture"
ms.assetid: 5cdc9396-a64b-4615-a1cd-b605db4c5983
caps.latest.revision: 12
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 11
---
# Ex&#233;cution d&#39;op&#233;rations de cha&#238;nes ind&#233;pendantes de la culture dans des collections
L'espace de noms <xref:System.Collections> contient des classes et des membres qui génèrent un comportement dépendant de la culture par défaut.  Les constructeurs par défaut des classes <xref:System.Collections.CaseInsensitiveComparer> et <xref:System.Collections.CaseInsensitiveHashCodeProvider> initialisent une nouvelle instance à l'aide de la propriété <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=fullName>.  Toutes les surcharges de la méthode [CollectionsUtil.CreateCaseInsensitiveHashTable](frlrfSystemCollectionsSpecializedCollectionsUtilClassCreateCaseInsensitiveHashtableTopic) créent une instance de la classe <xref:System.Collections.Hashtable> utilisant la propriété `Thread.CurrentCulture` par défaut.  Les surcharges de la méthode <xref:System.Collections.ArrayList.Sort%2A?displayProperty=fullName> effectuent des tris dépendants de la culture par défaut à l'aide de `Thread.CurrentCulture`.  Le tri et la consultation dans <xref:System.Collections.SortedList> peuvent être affectés par `Thread.CurrentCulture` lorsque des chaînes sont utilisées comme clés.  Suivez les recommandations d'utilisation contenues dans cette section pour obtenir des résultats indépendants de la culture de la part de ces classes et de ces méthodes dans l'espace de noms `Collections`.  
  
 **Remarque** Le passage de <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName> à une méthode de comparaison effectue une comparaison indépendante de la culture.  Toutefois, il n'entraîne pas de comparaison non linguistique, par exemple, pour les chemins d'accès de fichier, les clés de Registre et les variables d'environnement.  Il ne prend pas non plus en charge les décisions de sécurité basées sur le résultat de la comparaison.  Pour une comparaison non linguistique ou la prise en charge des décisions de sécurité dépendantes du résultat, l'application doit utiliser une méthode de comparaison qui accepte une valeur <xref:System.StringComparison>.  L'application doit ensuite passer <xref:System.StringComparison>.  
  
## Utilisation des classes CaseInsensitiveComparer et CaseInsensitiveHashCodeProvider  
 Les constructeurs par défaut pour `CaseInsensitiveHashCodeProvider` et `CaseInsensitiveComparer` initialisent une nouvelle instance de la classe à l'aide de `Thread.CurrentCulture`, ce qui se traduit par un comportement dépendant de la culture.  L'exemple de code suivant montre le constructeur d'une `Hashtable` dépendante de la culture parce qu'elle utilise les constructeurs par défaut pour `CaseInsensitiveHashCodeProvider` et `CaseInsensitiveComparer`.  
  
```vb  
internalHashtable = New Hashtable(CaseInsensitiveHashCodeProvider.Default, CaseInsensitiveComparer.Default)  
  
```  
  
```csharp  
internalHashtable = new Hashtable(CaseInsensitiveHashCodeProvider.Default, CaseInsensitiveComparer.Default);  
```  
  
 Si vous voulez créer une `Hashtable` indépendante de la culture à l'aide des classes `CaseInsensitiveComparer` et `CaseInsensitiveHashCodeProvider`, initialisez les nouvelles instances de ces classes à l'aide de constructeurs qui acceptent un paramètre `culture`.  Pour le paramètre `culture`, spécifiez <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>.  L'exemple de code suivant illustre le constructeur d'une `Hashtable` indépendante de la culture.  
  
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
  
## Utilisation de la méthode CollectionsUtil.CreateCaseInsensitiveHashTable  
 La méthode `CollectionsUtil.CreateCaseInsensitiveHashTable` est un raccourci utile pour la création d'une nouvelle instance de la classe `Hashtable` qui ignore la casse des chaînes.  Toutefois, toutes les surcharges de la méthode `CollectionsUtil.CreateCaseInsensitiveHashTable` sont dépendantes de la culture car elles utilisent la propriété `Thread.CurrentCulture`.  Vous ne pouvez pas créer de `Hashtable` indépendante de la culture à l'aide de cette méthode.  Pour créer une `Hashtable` indépendante de la culture, utilisez le constructeur `Hashtable` qui accepte un paramètre `culture`.  Pour le paramètre `culture`, spécifiez `CultureInfo.InvariantCulture`.  L'exemple de code suivant illustre le constructeur d'une `Hashtable` indépendante de la culture.  
  
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
## Utilisation de la classe SortedList  
 Un `SortedList` représente une collection de paires clé\/valeur triées par les clés et accessible par clé et par index.  Lorsque vous utilisez un `SortedList` où des chaînes sont les clés, le tri et la recherche peuvent être affectés par la propriété `Thread.CurrentCulture`.  Pour que le comportement de `SortedList` soit indépendant de la culture, créez un `SortedList` en utilisant l'un des constructeurs acceptant un paramètre `comparer`.  Le paramètre `comparer` indique l'implémentation <xref:System.Collections.IComparer> à utiliser lors de la comparaison de clés.  Pour le paramètre, spécifiez une classe de comparateur personnalisée qui utilise `CultureInfo.InvariantCulture` pour comparer les clés.  L'exemple suivant illustre une classe de comparateur personnalisé indépendant de la culture que vous pouvez spécifier comme paramètre `comparer` pour un constructeur `SortedList`.  
  
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
  
 En général, si vous utilisez `SortedList` sur des chaînes sans spécifier de comparateur personnalisé indifférent, un changement dans `Thread.CurrentCulture` une fois la liste remplie peut invalider cette liste.  
  
## Utilisation de la méthode ArrayList.Sort  
 Les surcharges de la méthode `ArrayList.Sort` effectuent des tris dépendants de la culture par défaut à l'aide de la propriété `Thread.CurrentCulture`.  Les résultats peuvent varier selon la culture, en raison des différents ordres de tri.  Pour supprimer cette dépendance à la culture, utilisez les surcharges de cette méthode acceptant une implémentation de `IComparer`.  Pour le paramètre `comparer`, spécifiez une classe de comparateur indifférent personnalisé qui utilise `CultureInfo.InvariantCulture`.  La rubrique [Utilisation de la classe SortedList](#cpconperformingculture-insensitivestringoperationsincollectionsanchor1) contient un exemple de classe de comparateur indifférent personnalisé.  
  
## Voir aussi  
 <xref:System.Collections.CaseInsensitiveComparer>   
 <xref:System.Collections.CaseInsensitiveHashCodeProvider>   
 <xref:System.Collections.ArrayList.Sort%2A?displayProperty=fullName>   
 <xref:System.Collections.SortedList>   
 <xref:System.Collections.Hashtable>   
 <xref:System.Collections.IComparer>   
 [Exécution d'opérations de chaînes indépendantes de la culture](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)   
 [Méthode CollectionsUtil.CreateCaseInsensitiveHashTable](frlrfSystemCollectionsSpecializedCollectionsUtilClassCreateCaseInsensitiveHashtableTopic)