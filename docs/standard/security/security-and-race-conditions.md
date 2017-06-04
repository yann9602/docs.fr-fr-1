---
title: "S&#233;curit&#233; et conditions de concurrence | Microsoft Docs"
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
  - "sécurité du code, conflits d'accès"
  - "conflits d'accès"
  - "codage sécurisé, conflits d'accès"
  - "sécurité (.NET Framework), conflits d'accès"
ms.assetid: ea3edb80-b2e8-4e85-bfed-311b20cb59b6
caps.latest.revision: 9
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 9
---
# S&#233;curit&#233; et conditions de concurrence
Un autre problème concerne les risques de brèches dans la sécurité et leur exploitation par des conditions de concurrence critique.  Ce problème peut se manifester de plusieurs façons :  Les sous\-rubriques suivantes mettent en avant certains des principaux pièges que le développeur doit éviter.  
  
## Conditions de concurrence critique dans la méthode Dispose  
 Si la méthode **Dispose** d'une classe \(consultez [Garbage Collection](../../../docs/standard/garbage-collection/index.md) pour plus d'informations\) n'est pas synchronisée, il est possible que le code de nettoyage à l'intérieur de **Dispose** soit exécuté plus d'une fois, comme illustré dans l'exemple suivant.  
  
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
  
 Comme cette implémentation **Dispose** n'est pas synchronisée, il est possible que `Cleanup` soit d'abord appelé par un thread puis par un deuxième thread avant que `_myObj` reçoive la valeur **null**.  Qu'il s'agisse d'un problème de sécurité ou non dépend du résultat de l'exécution du code `Cleanup`.  Un problème central lié aux implémentations **Dispose** synchronisées concerne l'utilisation de handles de ressource comme des fichiers par exemple.  Une suppression inappropriée peut entraîner l'utilisation d'un handle incorrect, ce qui génère souvent des failles en matière de sécurité.  
  
## Conditions de concurrence critique dans des constructeurs  
 Dans certaines applications, il est parfois possible pour d'autres threads d'accéder à des membres de la classe avant l'exécution complète de leurs constructeurs de classe.  Vous devez passer en revue tous les constructeurs de classe pour vous assurer qu'il n'y a pas de problème lié à la sécurité si cela doit se produire ou synchroniser des threads, si nécessaire.  
  
## Conditions de concurrence critique avec les objets mis en cache  
 Le code qui met en cache des informations de sécurité ou utilise l'opération [assertion](../../../docs/framework/misc/using-the-assert-method.md) de la sécurité d'accès du code peut être également soumis à des conditions de concurrence critique si d'autres parties de la classe ne sont pas correctement synchronisées, comme illustré dans l'exemple suivant.  
  
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
  
 S'il existe d'autres chemins vers `DoOtherWork` qui peuvent être appelés par un autre thread à l'aide du même objet, un appelant non fiable peut ignorer une demande sans la voir.  
  
 Si votre code met en cache des informations de sécurité, veillez à le passer en revue dans le cadre de cette faille.  
  
## Conditions de concurrence critique dans des finaliseurs  
 Des conditions de concurrence critique peuvent également se produire dans un objet qui référence une ressource statique ou non managée qu'il libère ensuite dans son finaliseur.  Si plusieurs objets partagent une ressource manipulée dans un finaliseur de classe, les objets doivent synchroniser tous les accès à cette ressource.  
  
## Voir aussi  
 [Instructions de codage sécurisé](../../../docs/standard/security/secure-coding-guidelines.md)