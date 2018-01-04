---
title: "Dispose, modèle"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Dispose method
- class library design guidelines [.NET Framework], Dispose method
- class library design guidelines [.NET Framework], Finalize method
- customizing Dispose method name
- Finalize method
ms.assetid: 31a6c13b-d6a2-492b-9a9f-e5238c983bcb
caps.latest.revision: "22"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 86fef5b18ac2c1c1b1dfee385b726484191fe714
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="dispose-pattern"></a>Dispose, modèle
Tous les programmes d’acquérir une ou plusieurs ressources système, telles que la mémoire, les handles du système ou les connexions de base de données, au cours de leur exécution. Les développeurs doivent être prudent lors de l’utilisation de ces ressources système, car ils doivent être libérées après que qu’ils ont été acquis et utilisés.  
  
 Le CLR prend en charge pour la gestion automatique de la mémoire. La mémoire managée (mémoire allouée à l’aide de l’opérateur c# `new`) n'a pas besoin d’être libérées de manière explicite. Il est publié automatiquement par le garbage collector (GC). Cela évite aux développeurs de la tâche fastidieuse et difficile de libération de mémoire et a été une des principales raisons de la productivité sans précédent offertes par le .NET Framework.  
  
 Malheureusement, la mémoire managée est simplement un des nombreux types de ressources système. Ressources autres que la mémoire managée toujours doivent être libérées explicitement et sont appelés les ressources non managées. Le catalogue global a été pas spécifiquement conçu pour gérer ces ressources non managées, ce qui signifie que la responsabilité de la gestion des ressources non managées se trouve entre les mains des développeurs.  
  
 Le CLR fournit une aide à la libération de ressources non managées. <xref:System.Object?displayProperty=nameWithType>déclare une méthode virtuelle <xref:System.Object.Finalize%2A> (également appelé le finaliseur) qui est appelée par le garbage collector avant que la mémoire de l’objet ne soit récupérée par le garbage collector et peut être substituée pour libérer les ressources non managées. Types de se substituer au finaliseur sont appelés types finalisables.  
  
 Bien que les finaliseurs sont efficaces dans certains scénarios de nettoyage, ils ont deux inconvénients importants :  
  
-   Le finaliseur est appelé lorsque le garbage collector détecte qu’un objet est éligible pour la collection. Cela se produit sur une période indéterminée de temps une fois que la ressource n’est plus nécessaire. Le délai entre lorsque le développeur peut ou souhaitez libérer la ressource et l’heure lorsque la ressource est libérée réellement par le finaliseur peut être inacceptable dans les programmes qui acquièrent de nombreuses ressources rares (les ressources qui peuvent être utilisées intégralement facilement) ou dans cas dans lequel les ressources sont coûteux à conserver en cours d’utilisation (par exemple, les tampons de grande taille de mémoire non managée).  
  
-   Lorsque le CLR a besoin d’appeler un finaliseur, il doit reporter la collecte de mémoire de l’objet jusqu'à ce que la prochaine arrondir du garbage collection (exécuter entre les collections les finaliseurs). Cela signifie que les mémoire de l’objet (et tous les objets qu’il fait référence au) ne seront pas libérées pour une période plus longue.  
  
 Par conséquent, exclusivement sur les finaliseurs de partie de confiance peut ne pas convenir dans de nombreux scénarios quand il est important de libérer les ressources non managées aussi rapidement que possible, lorsque vous traitez des ressources rares ou dans hautement performant scénarios dans lesquels la surcharge GC ajoutée de la finalisation n’est pas acceptable.  
  
 Le Framework fournit la <xref:System.IDisposable?displayProperty=nameWithType> interface qui doit être implémentée pour fournir aux développeurs un moyen manuel de libérer les ressources non managées, dès qu’ils ne sont pas nécessaires. Il fournit également la <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> méthode pouvant indiquer le garbage collector qui un objet a été supprimé manuellement et ne doive pas être finalisée, auquel cas la mémoire de l’objet peut être récupérée de plus haut. Les types qui implémentent la `IDisposable` interface sont considérés comme des types pouvant être supprimés.  
  
 Le modèle Dispose est destiné à normaliser l’utilisation et l’implémentation des finaliseurs et `IDisposable` interface.  
  
 La motivation principale pour le modèle consiste à réduire la complexité de l’implémentation de la <xref:System.Object.Finalize%2A> et <xref:System.IDisposable.Dispose%2A> méthodes. La complexité vient du fait que les méthodes partagent certains, mais pas tous les chemins de code (les différences sont décrites plus loin dans ce chapitre). En outre, il existe des raisons historiques pour certains éléments du modèle liés à l’évolution de la prise en charge linguistique pour la gestion des ressources déterministe.  
  
 **✓ FAIRE** implémenter le modèle de suppression de base sur les types contenant des instances de types pouvant être supprimés. Consultez le [base modèle Dispose](#basic_pattern) pour plus d’informations sur le modèle de base.  
  
 Si un type est chargé pour la durée de vie d’autres objets pouvant être supprimés, les développeurs ont besoin d’un moyen de les supprimer, trop. À l’aide du conteneur `Dispose` méthode est un moyen pratique de rend cela possible.  
  
 **✓ FAIRE** implémenter le modèle de suppression de base et de fournir un finaliseur sur les types de ressources d’exploitation qui doivent être libérées explicitement et qui n’ont pas de finaliseurs.  
  
 Par exemple, le modèle doit être implémenté sur les types de stockage des mémoires tampons de mémoire non managée. Le [Types finalisables](#finalizable_types) section décrit les instructions relatives à l’implémentation des finaliseurs.  
  
 **✓ Envisagez** implémentant le modèle de suppression de base sur les classes qu’eux-mêmes ne contiennent pas les ressources non managées ou les objets à supprimer, mais sont susceptibles d’avoir les sous-types de font.  
  
 Un bon exemple est la <xref:System.IO.Stream?displayProperty=nameWithType> classe. Bien qu’il soit une classe de base abstraite qui ne contient pas toutes les ressources, la plupart de ses sous-classes et pour cette raison, il implémente ce modèle.  
  
<a name="basic_pattern"></a>   
## <a name="basic-dispose-pattern"></a>Modèle de suppression de base  
 L’implémentation du modèle de base implique l’implémentation de la `System.IDisposable` interface et en déclarant le `Dispose(bool)` méthode qui implémente la logique de nettoyage toutes les ressources d’être partagées entre le `Dispose` (méthode) et le finaliseur facultatif.  
  
 L’exemple suivant montre une implémentation simple du modèle de base :  
  
```  
public class DisposableResourceHolder : IDisposable {  
  
    private SafeHandle resource; // handle to a resource  
  
    public DisposableResourceHolder(){  
        this.resource = ... // allocates the resource  
    }  
  
    public void Dispose(){  
        Dispose(true);  
        GC.SuppressFinalize(this);  
    }  
  
    protected virtual void Dispose(bool disposing){  
        if (disposing){  
            if (resource!= null) resource.Dispose();  
        }  
    }  
}  
```  
  
 Le paramètre booléen `disposing` indique si la méthode a été appelée à partir de la `IDisposable.Dispose` implémentation ou à partir du finaliseur. Le `Dispose(bool)` implémentation doit vérifier le paramètre avant d’accéder à d’autres objets de référence (par exemple, le champ de ressource dans l’exemple précédent). Ces objets doivent uniquement être utilisés lorsque la méthode est appelée à partir de la `IDisposable.Dispose` implémentation (lorsque le `disposing` paramètre est égal à true). Si la méthode est appelée depuis le finaliseur (`disposing` a la valeur false), autres objets ne doivent pas être accessibles. La raison est que les objets sont finalisés dans un ordre imprévisible et par conséquent, ils, ou une de ses dépendances, peut déjà avoir été finalisée.  
  
 En outre, cette section s’applique aux classes de base qui n’implémente pas déjà le modèle Dispose. Si vous héritez d’une classe qui implémente déjà le modèle, il vous suffit de remplacer le `Dispose(bool)` méthode pour fournir la logique de nettoyage des ressources supplémentaires.  
  
 **✓ FAIRE** déclarer un void virtuel protégé `Dispose(bool disposing)` méthode pour centraliser toute la logique associée à la libération des ressources non managées.  
  
 Nettoyage des ressources doit avoir lieu dans cette méthode. La méthode est appelée à partir de deux le finaliseur et `IDisposable.Dispose` (méthode). Le paramètre est false si l’appelé à partir d’à l’intérieur d’un finaliseur. Elle doit être utilisée pour vous assurer de n’importe quel code qui s’exécute pendant la finalisation n’accède pas aux autres objets finalisables. Détails de l’implémentation des finaliseurs sont décrits dans la section suivante.  
  
```  
protected virtual void Dispose(bool disposing){  
    if (disposing){  
        if (resource!= null) resource.Dispose();  
    }  
}  
```  
  
 **✓ FAIRE** implémenter la `IDisposable` interface en appelant simplement `Dispose(true)` suivie `GC.SuppressFinalize(this)`.  
  
 L’appel à `SuppressFinalize` doit se produire uniquement si `Dispose(true)` s’exécute avec succès.  
  
```  
public void Dispose(){  
    Dispose(true);  
    GC.SuppressFinalize(this);  
}  
```  
  
 **X ne sont pas** rendre sans paramètre `Dispose` méthode virtuelle.  
  
 Le `Dispose(bool)` méthode est celle qui doit être substituée par les sous-classes.  
  
```  
// bad design  
public class DisposableResourceHolder : IDisposable {  
    public virtual void Dispose(){ ... }  
    protected virtual void Dispose(bool disposing){ ... }  
}  
  
// good design  
public class DisposableResourceHolder : IDisposable {  
    public void Dispose(){ ... }  
    protected virtual void Dispose(bool disposing){ ... }  
}  
```  
  
 **X ne sont pas** déclarer toutes les surcharges de la `Dispose` autrement que `Dispose()` et `Dispose(bool)`.  
  
 `Dispose`Prenez en compte un mot réservé pour codifier ce modèle et éviter toute confusion entre les implémenteurs, les utilisateurs et les compilateurs. Certains langages peuvent choisir d’implémenter automatiquement ce modèle sur certains types.  
  
 **✓ FAIRE** autoriser la `Dispose(bool)` méthode à être appelée plusieurs fois. La méthode peut choisir de ne rien faire après le premier appel.  
  
```  
public class DisposableResourceHolder : IDisposable {  
  
    bool disposed = false;  
  
    protected virtual void Dispose(bool disposing){  
        if(disposed) return;  
        // cleanup  
        ...  
        disposed = true;  
    }  
}  
```  
  
 **X Évitez** lever une exception depuis `Dispose(bool)` sauf dans les situations où le processus de conteneur a été endommagé critiques (fuites, un état partagé incohérent, etc.).  
  
 Les utilisateurs s’attendent à qui un appel à `Dispose` ne lève pas d’exception.  
  
 Si `Dispose` peut lever une exception, la logique de nettoyage supplémentaire bloc finally n’exécutera pas. Pour contourner ce problème, l’utilisateur aurait besoin d’encapsuler chaque appel à `Dispose` (dans le bloc finally !) dans un bloc try, ce qui aboutit à des gestionnaires de nettoyage très complexe. Si l’exécution une `Dispose(bool disposing)` (méthode), jamais lève une exception si disposing a la valeur false. Cela va se terminer le processus s’exécute à l’intérieur d’un contexte de finaliseur.  
  
 **✓ FAIRE** lever un <xref:System.ObjectDisposedException> à partir de n’importe quel membre qui ne peut pas être utilisé une fois que l’objet a été supprimé.  
  
```  
public class DisposableResourceHolder : IDisposable {  
    bool disposed = false;  
    SafeHandle resource; // handle to a resource  
  
    public void DoSomething(){  
           if(disposed) throw new ObjectDisposedException(...);  
        // now call some native methods using the resource   
            ...  
    }  
    protected virtual void Dispose(bool disposing){  
        if(disposed) return;  
        // cleanup  
        ...  
        disposed = true;  
    }  
}  
```  
  
 **✓ Envisagez** en fournissant la méthode `Close()`, en plus de la `Dispose()`, si proche est une terminologie standard dans la zone.  
  
 Dans ce cas, il est important d’effectuer la `Close` implémentation identique à `Dispose` et implémentez la `IDisposable.Dispose` méthode explicitement.  
  
```  
public class Stream : IDisposable {  
    IDisposable.Dispose(){  
        Close();  
    }  
    public void Close(){  
        Dispose(true);  
        GC.SuppressFinalize(this);  
    }  
}  
```  
  
<a name="finalizable_types"></a>   
## <a name="finalizable-types"></a>Types finalisables  
 Types finalisables sont des types qui étendent le modèle de suppression de base en substituant le finaliseur et en fournissant le chemin d’accès du code de finalisation dans le `Dispose(bool)` (méthode).  
  
 Les finaliseurs sont notoirement difficiles à implémenter correctement, principalement du fait que vous ne pouvez apporter certaines hypothèses (normalement valides) sur l’état du système lors de leur exécution. Les instructions suivantes doivent être prises en considération prudence.  
  
 Notez que certaines instructions s’appliquent pas uniquement à la `Finalize` (méthode), mais à tout code appelé à partir d’un finaliseur. Dans le cas le modèle Dispose base défini précédemment, cela signifie que la logique qui s’exécute à l’intérieur de `Dispose(bool disposing)` lorsque le `disposing` paramètre a la valeur false.  
  
 Si la classe de base est finalisable déjà et implémente le modèle Dispose de base, vous ne devez pas substituer `Finalize` à nouveau. Vous devez substituer à la place simplement la `Dispose(bool)` méthode pour fournir la logique de nettoyage des ressources supplémentaires.  
  
 Le code suivant montre un exemple d’un type finalisable :  
  
```  
public class ComplexResourceHolder : IDisposable {  
  
    private IntPtr buffer; // unmanaged memory buffer  
    private SafeHandle resource; // disposable handle to a resource  
  
    public ComplexResourceHolder(){  
        this.buffer = ... // allocates memory  
        this.resource = ... // allocates the resource  
    }  
  
    protected virtual void Dispose(bool disposing){  
            ReleaseBuffer(buffer); // release unmanaged memory  
        if (disposing){ // release other disposable objects  
            if (resource!= null) resource.Dispose();  
        }  
    }  
  
    ~ ComplexResourceHolder(){  
        Dispose(false);  
    }  
  
    public void Dispose(){  
        Dispose(true);  
        GC.SuppressFinalize(this);  
    }  
}  
```  
  
 **X Évitez** rendre types finalisables.  
  
 Étudiez attentivement tout cas dans lequel vous pensez qu'un finaliseur est nécessaire. Il existe une véritable coût associé à des instances avec les finaliseurs, du point de vue à la fois une performance et la complexité. Préférez travailler avec des wrappers de ressources tels que <xref:System.Runtime.InteropServices.SafeHandle> pour encapsuler les ressources non managées lorsque cela est possible, auquel cas un finaliseur devienne inutile, car le wrapper est responsable de son propre nettoyage des ressources.  
  
 **X ne sont pas** rendre des types valeur finalisables.  
  
 Seuls les types référence réellement obtient finalisés par le CLR, et par conséquent, toute tentative visant à placer un finaliseur sur un type valeur sera ignorée. Les compilateurs c# et C++ appliquent cette règle.  
  
 **✓ FAIRE** rendre un type finalisables si le type est responsable de la libération d’une ressource non managée qui n’a pas son propre finaliseur.  
  
 Lorsque vous implémentez le finaliseur, appelez simplement `Dispose(false)` et placez la logique de nettoyage toutes les ressources à l’intérieur de la `Dispose(bool disposing)` (méthode).  
  
```  
public class ComplexResourceHolder : IDisposable {  
  
    ~ ComplexResourceHolder(){  
        Dispose(false);  
    }  
  
    protected virtual void Dispose(bool disposing){  
        ...  
    }  
}  
```  
  
 **✓ FAIRE** implémenter le modèle de suppression de base sur chaque type finalisable.  
  
 Cela permet aux utilisateurs du type pour effectuer explicitement le nettoyage déterministe de ces mêmes ressources dont le finaliseur est responsable.  
  
 **X ne sont pas** accéder à tous les objets finalisables dans le chemin d’accès du code finaliseur, étant donné le risque qu’ils seront déjà avoir été finalisés.  
  
 Par exemple, un objet finalisable A qui fait référence à un autre objet finalisable B ne peut pas utiliser fiable de B dans une suite de finaliseur, ou vice versa. Les finaliseurs sont appelés dans un ordre aléatoire (au niveau de la garantie de classement faible pour la finalisation critique).  
  
 En outre, sachez que les objets stockés dans des variables statiques seront collectés à certains points pendant un déchargement du domaine d’application ou lors de la sortie du processus. Accéder à une variable statique qui fait référence à un objet finalisable (ou en appelant une méthode statique qui peut utiliser des valeurs stockées dans des variables statiques) ne peut pas être sécurisé if <xref:System.Environment.HasShutdownStarted%2A?displayProperty=nameWithType> retourne la valeur true.  
  
 **✓ FAIRE** rendre votre `Finalize` méthode protégée.  
  
 Les développeurs c#, C++ et VB.NET est inutile à vous soucier de cette opération, car les compilateurs pour appliquer cette règle.  
  
 **X ne sont pas** échappement permettent d’exceptions à partir de la logique de finaliseur, à l’exception des défaillances système critiques.  
  
 Si une exception est levée à partir d’un finaliseur, le CLR s’arrête à l’ensemble du processus (à compter de .NET Framework version 2.0), empêchant d’autres finaliseurs d’exécuter et de ressources à partir de libéré de manière contrôlée.  
  
 **✓ Envisagez** création et utilisation d’un objet finalisable critiques (un type avec une hiérarchie de type qui contient <xref:System.Runtime.ConstrainedExecution.CriticalFinalizerObject>) pour les situations dans lesquelles un finaliseur absolument doit s’exécuter même en cas de déchargement de domaine d’application forcé et de thread abandonne.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*  
  
 *Réimprimées avec l’autorisation de Pearson éducation, Inc. à partir de [règles de conception d’infrastructure : Conventions, idiomes et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série de développement Microsoft Windows.*  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType>  
 <xref:System.Object.Finalize%2A?displayProperty=nameWithType>  
 [Règles de conception de .NET Framework](../../../docs/standard/design-guidelines/index.md)  
 [Modèles de design courants](../../../docs/standard/design-guidelines/common-design-patterns.md)  
 [Nettoyage de la mémoire](../../../docs/standard/garbage-collection/index.md)
