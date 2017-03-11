---
title: "Default property access is ambiguous between the inherited interface members &#39;&lt;defaultpropertyname&gt;&#39; of interface &#39;&lt;interfacename1&gt;&#39; and &#39;&lt;defaultpropertyname&gt;&#39; of interface &#39;&lt;interfacename2&gt;&#39; | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbc30686"
  - "bc30686"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30686"
ms.assetid: 784fefec-ef57-48cf-b960-957df419b439
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 13
---
# Default property access is ambiguous between the inherited interface members &#39;&lt;defaultpropertyname&gt;&#39; of interface &#39;&lt;interfacename1&gt;&#39; and &#39;&lt;defaultpropertyname&gt;&#39; of interface &#39;&lt;interfacename2&gt;&#39;
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Une interface hérite de deux interfaces, chacune déclarant une propriété par défaut avec le même nom.  Le compilateur ne peut pas résoudre un accès à cette propriété par défaut sans qualification.  L'exemple suivant illustre ce comportement.  
  
```  
Public Interface Iface1  
    Default Property prop(ByVal arg As Integer) As Integer  
End Interface  
Public Interface Iface2  
    Default Property prop(ByVal arg As Integer) As Integer  
End Interface  
Public Interface Iface3  
    Inherits Iface1, Iface2  
End Interface  
Public Class testClass  
    Public Sub accessDefaultProperty()  
        Dim testObj As Iface3  
        Dim testInt As Integer = testObj(1)  
    End Sub  
End Class  
```  
  
 Lorsque vous spécifiez `testObj(1)`, le compilateur tente de le résoudre en propriété par défaut.  Toutefois, puisqu'il existe deux propriétés par défaut possibles en raison des interfaces héritées, le compilateur signale cette erreur.  
  
 **ID d'erreur :** BC30686  
  
### Pour corriger cette erreur  
  
-   Évitez d'hériter des membres avec le même nom.  Dans l'exemple précédent, si `testObj` n'a pas besoin, par exemple, des membres de `Iface2`, déclarez\-le comme suit :  
  
    ```  
    Dim testObj As Iface1  
    ```  
  
     ou  
  
-   Implémentez l'interface qui hérite dans une classe.  Vous pouvez ensuite implémenter chacune des propriétés héritées avec des noms différents.  Toutefois, seule l'une d'entre elles peut être la propriété par défaut de la classe d'implémentation.  L'exemple suivant illustre ce comportement.  
  
    ```  
    Public Class useIface3  
        Implements Iface3  
        Default Public Property prop1(ByVal arg As Integer) As Integer Implements Iface1.prop  
            ' Insert code to define Get and Set procedures for prop1.  
        End Property  
        Public Property prop2(ByVal arg As Integer) As Integer Implements Iface2.prop  
            ' Insert code to define Get and Set procedures for prop2.  
        End Property  
    End Class  
    ```  
  
## Voir aussi  
 [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md)