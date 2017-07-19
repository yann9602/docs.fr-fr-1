---
title: "Mod&#232;le de suppression | Microsoft Docs"
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
helpviewer_keywords: 
  - "Dispose (méthode)"
  - "indications de conception de bibliothèques de classes (.NET Framework), Dispose (méthode)"
  - "indications de conception de bibliothèques de classes (.NET Framework), la méthode Finalize"
  - "personnalisation du nom de la méthode Dispose"
  - "Finalize (méthode)"
ms.assetid: 31a6c13b-d6a2-492b-9a9f-e5238c983bcb
caps.latest.revision: 22
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 22
---
# Mod&#232;le de suppression
Tous les programmes d’acquérir une ou plusieurs ressources système, telles que la mémoire, les handles du système ou les connexions de base de données, au cours de leur exécution. Les développeurs doivent être prudent lorsque vous utilisez ces ressources système, car ils doivent être libérés une fois qu’ils ont été acquis et utilisés.  
  
 Le CLR prend en charge pour la gestion automatique de la mémoire. Gestion de la mémoire \(mémoire allouée à l’aide de l’opérateur c\# `new`\) sans devoir être libérées de manière explicite. Il est libéré automatiquement par le garbage collector \(GC\). Cela évite aux développeurs de la tâche fastidieuse et difficile de libération de mémoire et a été une des principales raisons pour la productivité sans précédent offerte par .NET Framework.  
  
 Malheureusement, la mémoire managée est juste un des nombreux types de ressources système. Ressources autres que la mémoire managée toujours besoin d’être libérée explicitement et sont appelés les ressources non managées. Le catalogue global a été pas spécifiquement conçu pour gérer ces ressources non managées, ce qui signifie que la responsabilité de la gestion des ressources non managées se situe entre les mains des développeurs.  
  
 Le CLR fournit une aide à la libération de ressources non managées.<xref:System.Object?displayProperty=fullName> déclare une méthode virtuelle <xref:System.Object.Finalize%2A> \(également appelé le finaliseur\) qui est appelée par le garbage collector avant que la mémoire de l’objet ne soit récupérée par le garbage collector et peut être substituée pour libérer les ressources non managées. Les types qui substituent le finaliseur sont appelés types finalisables.  
  
 Bien que les finaliseurs sont efficaces dans certains scénarios de nettoyage, ils ont deux inconvénients importants :  
  
-   Le finaliseur est appelé lorsque le garbage collector détecte qu’un objet est éligible pour la collection. Cela se produit sur une certaine période indéterminée une fois que la ressource n’est plus nécessaire. Le délai entre lorsque le développeur pourrait ou souhaitez libérer la ressource et l’heure lorsque la ressource est libérée en fait par le finaliseur peut être inacceptable dans les programmes qui acquièrent plusieurs ressources rares \(les ressources qui peuvent être facilement épuisés\) ou dans les cas où les ressources sont coûteux à maintenir en cours d’utilisation \(par exemple, les tampons de grande mémoire non managée\).  
  
-   Lorsque le CLR doit appeler un finaliseur, il doit attendre la collection de la mémoire de l’objet suivant arrondit de garbage collection \(les finaliseurs s’exécutent entre les collections\). Cela signifie que les mémoire de l’objet \(et tous les objets qu’il fait référence à\) ne seront pas disponible pour une longue période de temps.  
  
 Par conséquent, utilisation exclusive de finaliseurs peut\-être pas appropriée dans de nombreux scénarios où il est important libérer les ressources non managées aussi rapidement que possible, lorsque vous traitez des ressources rares ou hautement performante les scénarios dans lesquels le GC ajouté une charge de finalisation est inacceptable.  
  
 L’infrastructure fournit le <xref:System.IDisposable?displayProperty=fullName> interface qui doit être implémentée pour fournir aux développeurs un moyen manuel de libérer des ressources non managées, dès qu’ils ne sont pas nécessaires. Il fournit également la <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> méthode que vous pouvez indiquer au GC qui un objet a été supprimé manuellement et n’a pas besoin d’être finalisé, auquel cas la mémoire de l’objet peut être récupérée de précédemment. Les types qui implémentent la `IDisposable` interface sont considérés comme des types jetables.  
  
 Le modèle Dispose est destiné à standardiser l’utilisation et l’implémentation des finaliseurs et `IDisposable` interface.  
  
 La raison principale pour le modèle consiste à réduire la complexité de l’implémentation de la <xref:System.Object.Finalize%2A> et le <xref:System.IDisposable.Dispose%2A> méthodes. La complexité vient du fait que les méthodes partagent certains mais pas tous les chemins de code \(les différences sont décrites plus loin dans ce chapitre\). En outre, il existe des raisons historiques pour certains éléments du modèle liés à l’évolution de la prise en charge linguistique pour la gestion des ressources déterministe.  
  
 **✓ faire** implémenter le modèle Dispose de base sur les types qui contient des instances des types jetables. Consultez le [base modèle Dispose](#basic_pattern) section pour plus d’informations sur le modèle de base.  
  
 Si un type est chargé de la durée de vie des autres objets jetables, les développeurs ont besoin d’un moyen de les supprimer, trop. À l’aide du conteneur `Dispose` méthode constitue un moyen pratique pour que cela soit possible.  
  
 **✓ faire** implémenter le modèle Dispose de base et de fournir un finaliseur sur les types de ressources d’exploitation qui doivent être libérées explicitement et qui n’ont pas de finaliseurs.  
  
 Par exemple, le modèle doit être implémenté sur les types de stockage des mémoires tampons de mémoire non managée. Le [Types finalisables](#finalizable_types) section décrit les instructions relatives à l’implémentation des finaliseurs.  
  
 **✓ envisagez** implémenter le modèle Dispose de base sur les classes qu’eux\-mêmes ne contiennent les ressources non managées ou des objets jetables, mais sont susceptibles d’avoir les sous\-types de font.  
  
 Un bon exemple de cela est la <xref:System.IO.Stream?displayProperty=fullName> classe. Bien qu’il soit une classe de base abstraite qui ne contient pas toutes les ressources, la plupart de ses sous\-classes et de ce fait, il implémente ce modèle.  
  
<a name="basic_pattern"></a>   
## Modèle de suppression de base  
 L’implémentation du modèle de base implique l’implémentation de la `System.IDisposable` interface et en déclarant le `Dispose(bool)` méthode qui implémente la logique de nettoyage toutes les ressources d’être partagées entre les `Dispose` méthode et le finaliseur facultatif.  
  
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
  
 Le paramètre booléen `disposing` indique si la méthode a été appelée à partir de la `IDisposable.Dispose` implémentation ou à partir du finaliseur. Le `Dispose(bool)` implémentation doit vérifier le paramètre avant d’accéder à d’autres objets de référence \(par exemple, le champ de ressource dans l’exemple précédent\). Ces objets accessibles uniquement lorsque la méthode est appelée à partir de la `IDisposable.Dispose` implémentation \(lorsque le `disposing` paramètre est égal à true\). Si la méthode est appelée à partir du finaliseur \(`disposing` a la valeur false\), autres objets ne doivent pas être accessibles. La raison est que les objets sont finalisés dans un ordre imprévisible et par conséquent, elles, ou l’un de leurs dépendances, peut déjà avoir été finalisé.  
  
 En outre, cette section s’applique aux classes de base qui n’implémentent pas déjà le modèle Dispose. Si vous héritez d’une classe qui implémente déjà le modèle, il vous suffit de remplacer le `Dispose(bool)` méthode pour fournir la logique de nettoyage des ressources supplémentaires.  
  
 **✓ faire** déclarer un void virtuels protégé `Dispose(bool disposing)` méthode pour centraliser toute la logique associée à la libération des ressources non managées.  
  
 Nettoyage des ressources doit avoir lieu dans cette méthode. La méthode est appelée à partir de deux le finaliseur et la `IDisposable.Dispose` \(méthode\). Le paramètre est false si est appelée depuis l’intérieur d’un finaliseur. Elle doit être utilisée afin de n’importe quel code qui s’exécute lors de la finalisation n’accède pas aux autres objets finalisables. Détails de l’implémentation des finaliseurs sont décrites dans la section suivante.  
  
```  
protected virtual void Dispose(bool disposing){  
    if (disposing){  
        if (resource!= null) resource.Dispose();  
    }  
}  
```  
  
 **✓ faire** implémenter la `IDisposable` interface en appelant simplement `Dispose(true)` suivie `GC.SuppressFinalize(this)`.  
  
 L’appel à `SuppressFinalize` doit se produire uniquement si `Dispose(true)` s’exécute correctement.  
  
```  
public void Dispose(){  
    Dispose(true);  
    GC.SuppressFinalize(this);  
}  
```  
  
 **X ne pas** rendre sans paramètre `Dispose` méthode virtuelle.  
  
 Le `Dispose(bool)` méthode est celle qui doit être substituée par les sous\-classes.  
  
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
  
 **X ne pas** déclare des surcharges de la `Dispose` méthode autre que `Dispose()` et `Dispose(bool)`.  
  
 `Dispose` Prenez un mot réservé pour codifier ce modèle et éviter toute confusion entre les implémenteurs, les utilisateurs et les compilateurs. Certains langages peuvent choisir d’implémenter automatiquement ce modèle sur certains types.  
  
 **✓ faire** permettre la `Dispose(bool)` méthode devant être appelée plusieurs fois. La méthode peut choisir de ne rien faire après le premier appel.  
  
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
  
 **X éviter** lever une exception depuis `Dispose(bool)` sauf dans les situations critiques où le processus contenant a été endommagé \(fuites, un état partagé incohérent, etc.\).  
  
 Les utilisateurs s’attendent à qui un appel à `Dispose` ne lève pas d’exception.  
  
 Si `Dispose` peut lever une exception, la logique de nettoyage bloc finally supplémentaire ne s’exécutera pas. Pour contourner ce problème, l’utilisateur aurait besoin d’encapsuler chaque appel à `Dispose` \(dans le bloc finally \!\) dans un bloc try, ce qui conduit à des gestionnaires de nettoyage très complexe. Si l’exécution un `Dispose(bool disposing)` \(méthode\), jamais lever une exception si disposing a la valeur false. Cela terminera le processus s’exécute à l’intérieur d’un contexte de finaliseur.  
  
 **✓ faire** lever un <xref:System.ObjectDisposedException> à partir de n’importe quel membre qui ne peut pas être utilisé après que l’objet a été supprimé.  
  
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
  
 **✓ envisagez** méthode `Close()`, en plus de la `Dispose()`, si proche est la terminologie standard dans la zone.  
  
 Lors de cette opération, il est important de faire la `Close` implémentation identique à `Dispose` et implémentez la `IDisposable.Dispose` méthode explicitement.  
  
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
## Types finalisables  
 Types finalisables sont des types qui étendent le modèle de base Dispose en substituant le finaliseur et en fournissant le chemin d’accès du code de finalisation dans le `Dispose(bool)` \(méthode\).  
  
 Les finaliseurs sont notoirement difficiles à implémenter correctement, principalement parce que vous ne pouvez apporter certaines hypothèses concernant l’état du système \(normalement valides\) pendant leur exécution. Les instructions suivantes doivent être prises en considération prudente.  
  
 Notez que certaines instructions s’appliquent pas uniquement à la `Finalize` \(méthode\), mais à tout code appelé à partir d’un finaliseur. Dans le cas le modèle Dispose base défini précédemment, cela signifie que la logique qui s’exécute à l’intérieur de `Dispose(bool disposing)` lorsque le `disposing` paramètre a la valeur false.  
  
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
  
 **X éviter** rendre types finalisables.  
  
 Étudiez attentivement tout cas dans lequel vous pensez qu'un finaliseur est nécessaire. Il existe une véritable coût associé aux instances avec des finaliseurs, une performance et le code de point de vue de la complexité. Préférez l’utilisation de wrappers de ressources tels que <xref:System.Runtime.InteropServices.SafeHandle> pour encapsuler les ressources non managées lorsque cela est possible, auquel cas un finaliseur devienne inutile, car le wrapper est responsable de son propre nettoyage des ressources.  
  
 **X ne pas** rendre les types valeur finalisable.  
  
 Seuls les types référence obtient réellement finalisés par le CLR, et ainsi toute tentative de placer un finaliseur dans un type valeur sera ignorée. Les compilateurs c\# et C\+\+ appliquent cette règle.  
  
 **✓ faire** rendre un type finalisable si le type est chargé de libérer une ressource non managée qui ne possède pas son propre finaliseur.  
  
 Lorsque vous implémentez le finaliseur, appelez simplement `Dispose(false)` et placer la logique de nettoyage toutes les ressources à l’intérieur de la `Dispose(bool disposing)` méthode.  
  
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
  
 **✓ faire** implémenter le modèle Dispose de base sur chaque type finalisable.  
  
 Cela permet aux utilisateurs de type pour effectuer explicitement le nettoyage déterministe de ces mêmes ressources dont le finaliseur est responsable.  
  
 **X ne pas** accéder aux objets finalisables dans le chemin d’accès du code finaliseur, étant donné le risque qu’ils seront déjà avoir été finalisés.  
  
 Par exemple, un objet finalisable A qui fait référence à un autre objet finalisable B ne peut pas utiliser fiable B dans le finaliseur, ou vice versa. Les finaliseurs sont appelés dans un ordre aléatoire \(court une garantie de classement faible pour la finalisation critique\).  
  
 En outre, n’oubliez pas que les objets stockés dans des variables statiques seront collectés à certains points pendant un déchargement du domaine d’application ou lors de la sortie du processus. L’accès à une variable statique qui fait référence à un objet finalisable \(ou appeler une méthode statique qui peut utiliser des valeurs stockées dans des variables statiques\) peuvent ne pas être sécurisé if <xref:System.Environment.HasShutdownStarted%2A?displayProperty=fullName> renvoie la valeur true.  
  
 **✓ faire** rendre votre `Finalize` méthode protégée.  
  
 Les développeurs c\#, C\+\+ et VB.NET inutile à vous soucier de cela, car les compilateurs pour appliquer cette règle.  
  
 **X ne pas** soustraites d’exceptions permettent à la logique de finaliseur, à l’exception des défaillances système critiques.  
  
 Si une exception est levée à partir d’un finaliseur, le CLR s’arrête le processus entier \(à compter de .NET Framework version 2.0\), empêchant les autres finaliseurs de l’exécution et les ressources libérées de façon contrôlée.  
  
 **✓ envisagez** création et utilisation d’un objet finalisable critique \(un type avec une hiérarchie de type qui contient <xref:System.Runtime.ConstrainedExecution.CriticalFinalizerObject>\) pour les situations dans lesquelles un finaliseur absolument doit s’exécuter même en cas de domaine d’application forcée décharge et les abandons de thread.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*  
  
 *Réimprimé avec l’autorisation de Pearson éducation, Inc. à partir de [Framework Design Guidelines : Conventions, langages et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison\-Wesley Professional dans le cadre de la série de développement de Microsoft Windows.*  
  
## Voir aussi  
 <xref:System.IDisposable.Dispose%2A?displayProperty=fullName>   
 <xref:System.Object.Finalize%2A?displayProperty=fullName>   
 [Instructions de conception d’infrastructure](../../../docs/standard/design-guidelines/index.md)   
 [Modèles de conception courants](../../../docs/standard/design-guidelines/common-design-patterns.md)   
 [Garbage Collection](../../../docs/standard/garbage-collection/index.md)