---
title: "Comment&#160;: cr&#233;er un objet WindowsPrincipal | Microsoft Docs"
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
  - "objets principaux, créer"
  - "sécurité (.NET Framework), créer un objet WindowsPrincipal"
  - "sécurité (.NET Framework), principaux"
  - "WindowsPrincipal (objets), créer"
ms.assetid: 56eb10ca-e61d-4ed2-af7a-555fc4c25a25
caps.latest.revision: 14
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 14
---
# Comment&#160;: cr&#233;er un objet WindowsPrincipal
Il existe deux façons de créer un objet <xref:System.Security.Principal.WindowsPrincipal>, selon que le code doit effectuer une ou plusieurs validations basées sur les rôles.  
  
 Si le code doit exécuter plusieurs validations basées sur les rôles, la première des procédures suivantes produira moins de surcharge.  Si le code ne doit exécuter qu'une seule validation basée sur les rôles, vous pouvez créer un objet <xref:System.Security.Principal.WindowsPrincipal> à l'aide de la deuxième procédure ci\-dessous.  
  
### Pour créer un objet WindowsPrincipal pour une validation répétée  
  
1.  Appelez la méthode <xref:System.AppDomain.SetPrincipalPolicy%2A> sur l'objet <xref:System.AppDomain> qui est retourné par la propriété statique <xref:System.AppDomain.CurrentDomain%2A?displayProperty=fullName>, en passant à la méthode une valeur d'énumération <xref:System.Security.Principal.PrincipalPolicy> qui indique la nouvelle stratégie.  Les valeurs prises en charge sont <xref:System.Security.Principal.PrincipalPolicy>, <xref:System.Security.Principal.PrincipalPolicy> et <xref:System.Security.Principal.PrincipalPolicy>.  Le code suivant illustre cet appel de méthode.  
  
    ```csharp  
    AppDomain.CurrentDomain.SetPrincipalPolicy(  
        PrincipalPolicy.WindowsPrincipal);  
    ```  
  
    ```vb  
    AppDomain.CurrentDomain.SetPrincipalPolicy( _  
        PrincipalPolicy.WindowsPrincipal)  
    ```  
  
2.  Une fois la stratégie définie, utilisez la propriété statique <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=fullName> pour récupérer le principal qui encapsule l'utilisateur Windows actuel.  Étant donné que le type de retour de la propriété est <xref:System.Security.Principal.IPrincipal>, vous devez caster le résultat vers un type <xref:System.Security.Principal.WindowsPrincipal>.  Le code suivant initialise un nouvel objet <xref:System.Security.Principal.WindowsPrincipal> vers la valeur du principal associé au thread actuel.  
  
    ```csharp  
    WindowsPrincipal MyPrincipal =   
        (WindowsPrincipal) Thread.CurrentPrincipal;  
    ```  
  
    ```vb  
    Dim MyPrincipal As WindowsPrincipal = _  
        CType(Thread.CurrentPrincipal, WindowsPrincipal)   
    ```  
  
3.  Quand l'objet principal a été créé, vous pouvez utiliser plusieurs méthodes pour le valider.  
  
### Pour créer un objet WindowsPrincipal pour une validation unique  
  
1.  Initialisez un nouvel objet <xref:System.Security.Principal.WindowsIdentity> en appelant la méthode statique <xref:System.Security.Principal.WindowsIdentity.GetCurrent%2A?displayProperty=fullName>, qui interroge le compte Windows actuel et place des informations sur ce compte dans l'objet d'identité récemment créé.  Le code suivant crée un nouvel objet <xref:System.Security.Principal.WindowsIdentity> et l'initialise vers l'utilisateur authentifié actuel.  
  
    ```csharp  
    WindowsIdentity MyIdentity = WindowsIdentity.GetCurrent();  
    ```  
  
    ```vb  
    Dim MyIdentity As WindowsIdentity = WindowsIdentity.GetCurrent()  
    ```  
  
2.  Créez un objet <xref:System.Security.Principal.WindowsPrincipal> et passez\-lui la valeur de l'objet <xref:System.Security.Principal.WindowsIdentity> créé à l'étape précédente.  
  
    ```csharp  
    WindowsPrincipal MyPrincipal = new WindowsPrincipal(MyIdentity);  
    ```  
  
    ```vb  
    Dim MyPrincipal As New WindowsPrincipal(MyIdentity)  
    ```  
  
3.  Quand l'objet principal a été créé, vous pouvez utiliser plusieurs méthodes pour le valider.  
  
## Voir aussi  
 [Objets Principal et Identity](../../../docs/standard/security/principal-and-identity-objects.md)