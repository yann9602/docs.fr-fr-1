---
title: "Emprunt et restauration d&#39;identit&#233; | Microsoft Docs"
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
  - "emprunter l'identité de comptes Windows"
  - "sécurité (.NET Framework), emprunter l'identité de comptes Windows"
  - "WindowsIdentity (objets), emprunter l'identité"
ms.assetid: b93d402c-6c28-4f50-b2bc-d9607dc3e470
caps.latest.revision: 13
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 11
---
# Emprunt et restauration d&#39;identit&#233;
Parfois, vous devez obtenir un jeton de compte Windows NT pour emprunter l’identité d’un compte Windows. Par exemple, votre application ASP.NET peut devoir agir pour le compte de plusieurs utilisateurs à des moments différents. Votre application peut accepter un jeton représentant un administrateur à partir d’Internet Information Services \(IIS\), emprunter l’identité de cet utilisateur, effectuer une opération et revenir à l’identité précédente. Ensuite, elle peut accepter un jeton d’IIS représentant un utilisateur disposant de droits inférieurs, effectuer une opération et revenir à nouveau à l’identité précédente.  
  
 Dans les situations où votre application doit emprunter l’identité d’un compte Windows qui n’a pas été attaché au thread actuel par IIS, vous devez extraire le jeton du compte et l’utiliser pour activer le compte. Pour cela, procédez comme suit :  
  
1.  Récupérez le jeton de compte pour un utilisateur particulier en appelant la méthode **LogonUser** non managée. Cette méthode ne figure pas dans la bibliothèque de classes de base du .NET Framework, mais dans le fichier **advapi32.dll** non managé. L’accès aux méthodes dans du code non managé est une opération complexe qui dépasse le cadre de cette discussion. Pour plus d’informations, consultez [Interopération avec du code non managé](../../../docs/framework/interop/index.md). Pour plus d’informations sur la méthode **LogonUser** et **advapi32.dll**, consultez la documentation du SDK de la plateforme.  
  
2.  Créez une nouvelle instance de la classe **WindowsIdentity**, qui passe le jeton. Le code suivant illustre cet appel, où `hToken` désigne un jeton Windows.  
  
    ```csharp  
    WindowsIdentity ImpersonatedIdentity = new WindowsIdentity(hToken);  
  
    ```  
  
    ```vb  
    Dim ImpersonatedIdentity As New WindowsIdentity(hToken)  
    ```  
  
3.  Commencez l’emprunt d’identité en créant une instance de la classe <xref:System.Security.Principal.WindowsImpersonationContext> et en l’initialisant avec la méthode <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A?displayProperty=fullName> de la classe initialisée, comme illustré dans le code suivant.  
  
    ```csharp  
    WindowsImpersonationContext MyImpersonation = ImpersonatedIdentity.Impersonate();  
  
    ```  
  
    ```vb  
    WindowsImpersonationContext MyImpersonation = ImpersonatedIdentity.Impersonate()  
    ```  
  
4.  Quand vous n’avez plus besoin d’emprunter l’identité, appelez la méthode <xref:System.Security.Principal.WindowsImpersonationContext.Undo%2A?displayProperty=fullName> pour rétablir l’emprunt d’identité, comme illustré dans le code suivant.  
  
    ```csharp  
    MyImpersonation.Undo();  
  
    ```  
  
    ```vb  
    MyImpersonation.Undo()  
    ```  
  
 Si du code approuvé a déjà attaché un objet <xref:System.Security.Principal.WindowsPrincipal> au thread, vous pouvez appeler la méthode d’instance **Impersonate**, qui n’accepte pas de jeton de compte. Notez que cela est utile uniquement quand l’objet **WindowsPrincipal** sur le thread représente un utilisateur autre que celui sous lequel le processus est exécuté. Par exemple, vous pouvez rencontrer cette situation quand vous utilisez ASP.NET avec l’authentification Windows activée et l’emprunt d’identité désactivé. Dans ce cas, le processus s’exécute sous un compte configuré dans Internet Information Services \(IIS\), tandis que le principal actuel représente l’utilisateur Windows qui accède à la page.  
  
 Notez que ni **Impersonate** ni **Undo** ne modifie l’objet **Principal** \(<xref:System.Security.Principal.IPrincipal>\) associé au contexte d’appel actuel. Au lieu de cela, l’emprunt d’identité et le rétablissement modifient le jeton associé au processus de système d’exploitation actuel.  
  
## Voir aussi  
 <xref:System.Security.Principal.WindowsIdentity>   
 <xref:System.Security.Principal.WindowsImpersonationContext>   
 [Objets Principal et Identity](../../../docs/standard/security/principal-and-identity-objects.md)   
 [Interoperating with Unmanaged Code](../../../docs/framework/interop/index.md)