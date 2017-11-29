---
title: "Sécurité et conditions de concurrence"
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
- security [.NET Framework], race conditions
- race conditions
- secure coding, race conditions
- code security, race conditions
ms.assetid: ea3edb80-b2e8-4e85-bfed-311b20cb59b6
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c092113f670c5799d98dcb13c9c713bbd1a47fb6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="security-and-race-conditions"></a><span data-ttu-id="61a65-102">Sécurité et conditions de concurrence</span><span class="sxs-lookup"><span data-stu-id="61a65-102">Security and Race Conditions</span></span>
<span data-ttu-id="61a65-103">Un autre problème concerne le risque de failles de sécurité exploité par des conditions de concurrence.</span><span class="sxs-lookup"><span data-stu-id="61a65-103">Another area of concern is the potential for security holes exploited by race conditions.</span></span> <span data-ttu-id="61a65-104">Il existe plusieurs façons dans lequel cela peut se produire.</span><span class="sxs-lookup"><span data-stu-id="61a65-104">There are several ways in which this might happen.</span></span> <span data-ttu-id="61a65-105">Les sous-rubriques qui suivent décrivent certains des principaux pièges que le développeur doit éviter.</span><span class="sxs-lookup"><span data-stu-id="61a65-105">The subtopics that follow outline some of the major pitfalls that the developer must avoid.</span></span>  
  
## <a name="race-conditions-in-the-dispose-method"></a><span data-ttu-id="61a65-106">Conditions de concurrence dans la méthode Dispose</span><span class="sxs-lookup"><span data-stu-id="61a65-106">Race Conditions in the Dispose Method</span></span>  
 <span data-ttu-id="61a65-107">Si une classe de **Dispose** (méthode) (pour plus d’informations, consultez [le Garbage Collection](../../../docs/standard/garbage-collection/index.md)) est non synchronisé, il est possible que le code de nettoyage à l’intérieur de **Dispose** peut être exécutée plus de fois, comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="61a65-107">If a class's **Dispose** method (for more information, see [Garbage Collection](../../../docs/standard/garbage-collection/index.md)) is not synchronized, it is possible that cleanup code inside **Dispose** can be run more than once, as shown in the following example.</span></span>  
  
```vb  
Sub Dispose()  
    If Not (myObj Is Nothing) Then  
       Cleanup(myObj)  
       myObj = Nothing  
    End If  
End Sub  
```  
  
```csharp  
void Dispose()   
{  
    if( myObj != null )   
    {  
        Cleanup(myObj);  
        myObj = null;  
    }  
}  
```  
  
 <span data-ttu-id="61a65-108">Étant donné que cela **Dispose** implémentation n’est pas synchronisée, il est possible pour `Cleanup` à être appelé par tout d’abord un thread, puis un deuxième thread avant `_myObj` a la valeur **null**.</span><span class="sxs-lookup"><span data-stu-id="61a65-108">Because this **Dispose** implementation is not synchronized, it is possible for `Cleanup` to be called by first one thread and then a second thread before `_myObj` is set to **null**.</span></span> <span data-ttu-id="61a65-109">S’il s’agit d’un problème de sécurité dépend de ce qui se passe lorsque le `Cleanup` code s’exécute.</span><span class="sxs-lookup"><span data-stu-id="61a65-109">Whether this is a security concern depends on what happens when the `Cleanup` code runs.</span></span> <span data-ttu-id="61a65-110">Un problème majeur avec non synchronisés **Dispose** implémentations implique l’utilisation de handles de ressource tels que les fichiers.</span><span class="sxs-lookup"><span data-stu-id="61a65-110">A major issue with unsynchronized **Dispose** implementations involves the use of resource handles such as files.</span></span> <span data-ttu-id="61a65-111">Suppression inappropriée peut entraîner le handle incorrect à utiliser, ce qui conduit souvent à des failles de sécurité.</span><span class="sxs-lookup"><span data-stu-id="61a65-111">Improper disposal can cause the wrong handle to be used, which often leads to security vulnerabilities.</span></span>  
  
## <a name="race-conditions-in-constructors"></a><span data-ttu-id="61a65-112">Conditions de concurrence dans les constructeurs</span><span class="sxs-lookup"><span data-stu-id="61a65-112">Race Conditions in Constructors</span></span>  
 <span data-ttu-id="61a65-113">Dans certaines applications, il peut être possible d’autres threads peuvent accéder aux membres de la classe avant l’exécution complète de leurs constructeurs de classe.</span><span class="sxs-lookup"><span data-stu-id="61a65-113">In some applications, it might be possible for other threads to access class members before their class constructors have completely run.</span></span> <span data-ttu-id="61a65-114">Vous devez passer en revue tous les constructeurs de classe pour vous assurer qu’il n’y a aucun problème de sécurité si cela doit se produire ou synchroniser des threads si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="61a65-114">You should review all class constructors to make sure that there are no security issues if this should happen, or synchronize threads if necessary.</span></span>  
  
## <a name="race-conditions-with-cached-objects"></a><span data-ttu-id="61a65-115">Conditions de concurrence avec les objets mis en cache</span><span class="sxs-lookup"><span data-stu-id="61a65-115">Race Conditions with Cached Objects</span></span>  
 <span data-ttu-id="61a65-116">Code qui met en cache les informations de sécurité ou qui utilise la sécurité d’accès du code [Assert](../../../docs/framework/misc/using-the-assert-method.md) opération peut également être vulnérable aux conditions de concurrence critique si d’autres parties de la classe ne sont pas correctement synchronisées, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="61a65-116">Code that caches security information or uses the code access security [Assert](../../../docs/framework/misc/using-the-assert-method.md) operation might also be vulnerable to race conditions if other parts of the class are not appropriately synchronized, as shown in the following example.</span></span>  
  
```vb  
Sub SomeSecureFunction()  
    If SomeDemandPasses() Then  
        fCallersOk = True  
        DoOtherWork()  
        fCallersOk = False()  
    End If  
End Sub  
  
Sub DoOtherWork()  
    If fCallersOK Then  
        DoSomethingTrusted()  
    Else  
        DemandSomething()  
        DoSomethingTrusted()  
    End If  
End Sub  
```  
  
```csharp  
void SomeSecureFunction()   
{  
    if(SomeDemandPasses())   
    {  
        fCallersOk = true;  
        DoOtherWork();  
        fCallersOk = false();  
    }  
}  
void DoOtherWork()   
{  
    if( fCallersOK )   
    {  
        DoSomethingTrusted();  
    }  
    else   
    {  
        DemandSomething();  
        DoSomethingTrusted();  
    }  
}  
```  
  
 <span data-ttu-id="61a65-117">S’il existe d’autres chemins pour `DoOtherWork` qui peut être appelée à partir d’un autre thread avec le même objet, un appelant non fiable peut ignorer une demande.</span><span class="sxs-lookup"><span data-stu-id="61a65-117">If there are other paths to `DoOtherWork` that can be called from another thread with the same object, an untrusted caller can slip past a demand.</span></span>  
  
 <span data-ttu-id="61a65-118">Si votre code met en cache les informations de sécurité, assurez-vous que vous l’examinez cette vulnérabilité.</span><span class="sxs-lookup"><span data-stu-id="61a65-118">If your code caches security information, make sure that you review it for this vulnerability.</span></span>  
  
## <a name="race-conditions-in-finalizers"></a><span data-ttu-id="61a65-119">Conditions de concurrence dans les finaliseurs</span><span class="sxs-lookup"><span data-stu-id="61a65-119">Race Conditions in Finalizers</span></span>  
 <span data-ttu-id="61a65-120">Conditions de concurrence peuvent également se produire dans un objet qui fait référence à une ressource statique ou non managée qu’il libère ensuite dans son finaliseur.</span><span class="sxs-lookup"><span data-stu-id="61a65-120">Race conditions can also occur in an object that references a static or unmanaged resource that it then frees in its finalizer.</span></span> <span data-ttu-id="61a65-121">Si plusieurs objets partagent une ressource manipulée dans un finaliseur de classe, les objets doivent synchroniser tous les accès à cette ressource.</span><span class="sxs-lookup"><span data-stu-id="61a65-121">If multiple objects share a resource that is manipulated in a class's finalizer, the objects must synchronize all access to that resource.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61a65-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="61a65-122">See Also</span></span>  
 [<span data-ttu-id="61a65-123">Instructions de codage sécurisé</span><span class="sxs-lookup"><span data-stu-id="61a65-123">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
