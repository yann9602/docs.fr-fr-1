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
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 73664df9c072189f11d451da46bc3019c8593ec9
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="security-and-race-conditions"></a>Sécurité et conditions de concurrence
Un autre problème concerne le risque de failles de sécurité exploité par des conditions de concurrence. Il existe plusieurs façons dans lequel cela peut se produire. Les sous-rubriques qui suivent décrivent certains des principaux pièges que le développeur doit éviter.  
  
## <a name="race-conditions-in-the-dispose-method"></a>Conditions de concurrence dans la méthode Dispose  
 Si une classe de **Dispose** (méthode) (pour plus d’informations, consultez [le Garbage Collection](../../../docs/standard/garbage-collection/index.md)) est non synchronisé, il est possible que le code de nettoyage à l’intérieur de **Dispose** peut être exécutée plus de fois, comme illustré dans l’exemple suivant.  
  
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
  
 Étant donné que cela **Dispose** implémentation n’est pas synchronisée, il est possible pour `Cleanup` à être appelé par tout d’abord un thread, puis un deuxième thread avant `_myObj` a la valeur **null**. S’il s’agit d’un problème de sécurité dépend de ce qui se passe lorsque le `Cleanup` code s’exécute. Un problème majeur avec non synchronisés **Dispose** implémentations implique l’utilisation de handles de ressource tels que les fichiers. Suppression inappropriée peut entraîner le handle incorrect à utiliser, ce qui conduit souvent à des failles de sécurité.  
  
## <a name="race-conditions-in-constructors"></a>Conditions de concurrence dans les constructeurs  
 Dans certaines applications, il peut être possible d’autres threads peuvent accéder aux membres de la classe avant l’exécution complète de leurs constructeurs de classe. Vous devez passer en revue tous les constructeurs de classe pour vous assurer qu’il n’y a aucun problème de sécurité si cela doit se produire ou synchroniser des threads si nécessaire.  
  
## <a name="race-conditions-with-cached-objects"></a>Conditions de concurrence avec les objets mis en cache  
 Code qui met en cache les informations de sécurité ou qui utilise la sécurité d’accès du code [Assert](../../../docs/framework/misc/using-the-assert-method.md) opération peut également être vulnérable aux conditions de concurrence critique si d’autres parties de la classe ne sont pas correctement synchronisées, comme indiqué dans l’exemple suivant.  
  
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
  
 S’il existe d’autres chemins pour `DoOtherWork` qui peut être appelée à partir d’un autre thread avec le même objet, un appelant non fiable peut ignorer une demande.  
  
 Si votre code met en cache les informations de sécurité, assurez-vous que vous l’examinez cette vulnérabilité.  
  
## <a name="race-conditions-in-finalizers"></a>Conditions de concurrence dans les finaliseurs  
 Conditions de concurrence peuvent également se produire dans un objet qui fait référence à une ressource statique ou non managée qu’il libère ensuite dans son finaliseur. Si plusieurs objets partagent une ressource manipulée dans un finaliseur de classe, les objets doivent synchroniser tous les accès à cette ressource.  
  
## <a name="see-also"></a>Voir aussi  
 [Instructions de codage sécurisé](../../../docs/standard/security/secure-coding-guidelines.md)
