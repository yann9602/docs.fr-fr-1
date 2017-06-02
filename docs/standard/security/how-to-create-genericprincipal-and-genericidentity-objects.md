---
title: "Comment&#160;: cr&#233;er des objets GenericPrincipal et GenericIdentity | Microsoft Docs"
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
  - "créer des objets Identity génériques"
  - "créer des objets GenericPrincipal"
  - "GenericIdentity (objets)"
  - "GenericPrincipal (objets)"
ms.assetid: 465694cf-258b-4747-9dae-35b01a5bcdbb
caps.latest.revision: 10
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 8
---
# Comment&#160;: cr&#233;er des objets GenericPrincipal et GenericIdentity
Vous pouvez utiliser la classe <xref:System.Security.Principal.GenericIdentity> conjointement avec la classe <xref:System.Security.Principal.GenericPrincipal> pour créer une stratégie d'autorisation indépendante d'un domaine Windows NT ou Windows 2000.  
  
### Pour créer un objet GenericPrincipal  
  
1.  Créez une nouvelle instance de la classe Identity et initialisez\-la à l'aide du nom voulu.  Le code suivant crée un nouvel objet **GenericIdentity** et lui assigne le nom `MyUser`.  
  
    ```vb  
    Dim MyIdentity As New GenericIdentity("MyUser")  
    ```  
  
    ```csharp  
    GenericIdentity MyIdentity = new GenericIdentity("MyUser");  
    ```  
  
2.  Créez une nouvelle instance de la classe **GenericPrincipal** et initialisez\-la avec l'objet **GenericIdentity** précédemment créé et un tableau de chaînes représentant les rôles à associer à cette entité de sécurité.  L'exemple de code suivant spécifie un tableau de chaînes qui représentent un rôle d'administrateur et un rôle d'utilisateur.  La classe **GenericPrincipal** est ensuite initialisée avec l'objet **GenericIdentity** précédent et le tableau de chaînes.  
  
    ```vb  
    Dim MyStringArray As String() = {"Manager", "Teller"}  
    DIm MyPrincipal As New GenericPrincipal(MyIdentity, MyStringArray)  
    ```  
  
    ```csharp  
    String[] MyStringArray = {"Manager", "Teller"};  
    GenericPrincipal MyPrincipal = new GenericPrincipal(MyIdentity, MyStringArray);  
    ```  
  
3.  Utilisez le code suivant pour attacher l'entité de sécurité au thread en cours.  Cette procédure s'avère utile lorsque l'entité de sécurité doit être validée à plusieurs reprises ou encore lorsqu'elle doit être validée par un autre code exécuté dans votre application ou par un objet <xref:System.Security.Permissions.PrincipalPermission>.  Vous pouvez effectuer une validation basée sur les rôles sur l'objet Principal sans l'attacher au thread.  Pour plus d'informations, consultez [Remplacement d'un objet Principal](../../../docs/standard/security/replacing-a-principal-object.md).  
  
    ```vb  
    Thread.CurrentPrincipal = MyPrincipal  
    ```  
  
    ```csharp  
    Thread.CurrentPrincipal = MyPrincipal;  
    ```  
  
## Exemple  
 L'exemple de code suivant montre comment créer une instance de classe **GenericPrincipal** et **GenericIdentity**.  Le code affiche les valeurs de ces objets dans la console.  
  
```vb  
Imports System  
Imports System.Security.Principal  
Imports System.Threading  
  
Public Class Class1  
  
    Public Shared Sub Main()  
        ' Create generic identity.  
        Dim MyIdentity As New GenericIdentity("MyIdentity")  
  
        ' Create generic principal.  
        Dim MyStringArray As String() =  {"Manager", "Teller"}  
        Dim MyPrincipal As New GenericPrincipal(MyIdentity, MyStringArray)  
  
        ' Attach the principal to the current thread.  
        ' This is not required unless repeated validation must occur,  
        ' other code in your application must validate, or the   
        ' PrincipalPermisson object is used.   
        Thread.CurrentPrincipal = MyPrincipal  
  
        ' Print values to the console.  
        Dim Name As String = MyPrincipal.Identity.Name  
        Dim Auth As Boolean = MyPrincipal.Identity.IsAuthenticated  
        Dim IsInRole As Boolean = MyPrincipal.IsInRole("Manager")  
  
        Console.WriteLine("The Name is: {0}", Name)  
        Console.WriteLine("The IsAuthenticated is: {0}", Auth)  
        Console.WriteLine("Is this a Manager? {0}", IsInRole)  
  
    End Sub  
  
End Class  
```  
  
```csharp  
using System;  
using System.Security.Principal;  
using System.Threading;  
  
public class Class1  
{  
    public static int Main(string[] args)  
    {  
    // Create generic identity.  
    GenericIdentity MyIdentity = new GenericIdentity("MyIdentity");  
  
    // Create generic principal.  
    String[] MyStringArray = {"Manager", "Teller"};  
    GenericPrincipal MyPrincipal =   
        new GenericPrincipal(MyIdentity, MyStringArray);  
  
    // Attach the principal to the current thread.  
    // This is not required unless repeated validation must occur,  
    // other code in your application must validate, or the   
    // PrincipalPermisson object is used.   
    Thread.CurrentPrincipal = MyPrincipal;  
  
    // Print values to the console.  
    String Name =  MyPrincipal.Identity.Name;  
    bool Auth =  MyPrincipal.Identity.IsAuthenticated;   
    bool IsInRole =  MyPrincipal.IsInRole("Manager");  
  
    Console.WriteLine("The Name is: {0}", Name);  
    Console.WriteLine("The IsAuthenticated is: {0}", Auth);  
    Console.WriteLine("Is this a Manager? {0}", IsInRole);  
  
    return 0;  
    }  
}  
```  
  
 Lors de l'exécution, la sortie affichée par l'application se présente sous le format suivant :  
  
```  
The Name is: MyIdentity  
The IsAuthenticated is: True  
Is this a Manager? True  
```  
  
## Voir aussi  
 <xref:System.Security.Principal.GenericIdentity>   
 <xref:System.Security.Principal.GenericPrincipal>   
 <xref:System.Security.Permissions.PrincipalPermission>   
 [Remplacement d'un objet Principal](../../../docs/standard/security/replacing-a-principal-object.md)   
 [Objets Principal et Identity](../../../docs/standard/security/principal-and-identity-objects.md)