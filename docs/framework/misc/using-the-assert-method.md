---
title: "Utilisation de la méthode Assert"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- granting permissions, overriding security checks
- code access security, overriding security checks
- overriding security checks
- security [.NET Framework], overriding security checks
- security [.NET Framework], assertions
- asserted permissions
- Assert method
- caller security checks
- permissions [.NET Framework], overriding security checks
- permissions [.NET Framework], assertions
ms.assetid: 1e40f4d3-fb7d-4f19-b334-b6076d469ea9
caps.latest.revision: "20"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a1627af9dd968a8a183a251d5352c62457f71e27
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="using-the-assert-method"></a>Utilisation de la méthode Assert
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <xref:System.Security.CodeAccessPermission.Assert%2A> est une méthode qui peut être appelée sur les classes d'autorisation d'accès au code et sur la classe <xref:System.Security.PermissionSet>. Vous pouvez utiliser **Assert** pour activer votre code (et aux appelants en aval) effectuer des actions que votre code est autorisé à faire mais ses appelants ne soyez pas autorisé à faire. Une assertion de sécurité modifie le processus normal de vérification de sécurité effectué par le runtime. Lors de l'assertion d'une autorisation, le système de sécurité reçoit l'ordre de ne pas vérifier que les appelants de votre code disposent de l'autorisation ayant fait l'objet d'une assertion.  
  
> [!CAUTION]
>  Utilisez les assertions avec précaution, car elles peuvent ouvrir des failles de sécurité et perturber le mécanisme d'application des restrictions de sécurité du runtime.  
  
 Les assertions sont utiles quand une bibliothèque appelle du code non managé ou effectue un appel qui nécessite une autorisation qui n'est pas liée de manière évidente à l'utilisation prévue de la bibliothèque. Par exemple, tout code managé qui appelle dans du code non managé doit posséder **SecurityPermission** avec la **UnmanagedCode** indicateur spécifié. Par défaut, le code qui ne provient pas de l'ordinateur local, comme le code téléchargé à partir de l'intranet local, ne recevra pas cette autorisation. Par conséquent, pour que le code téléchargé à partir de l'intranet local puisse appeler une bibliothèque qui utilise du code non managé, il doit disposer de l'autorisation ayant fait l'objet d'une assertion effectuée par la bibliothèque. En outre, certaines bibliothèques peuvent effectuer des appels invisibles aux appelants et nécessitent donc des autorisations spéciales.  
  
 Vous pouvez également utiliser des assertions quand votre code accède à une ressource d'une manière totalement invisible pour les appelants. Supposons, par exemple, que votre bibliothèque obtienne des informations d'une base de données, mais que, pendant le processus, elle lise également les informations du Registre de l'ordinateur. Étant donné que les développeurs qui utilisent votre bibliothèque n’ont pas d’accès à votre source, ils n’ont aucun moyen de savoir que leur code nécessite **RegistryPermission** pour pouvoir utiliser votre code. Dans ce cas, si vous décidez qu'il n'est pas raisonnable ni nécessaire d'exiger que les appelants de votre code aient l'autorisation d'accéder au Registre, vous pouvez procéder à l'assertion de l'autorisation pour la lecture du Registre. Dans ce cas, il convient de la bibliothèque à déclarer l’autorisation ainsi que les appelants **RegistryPermission** pouvez utiliser la bibliothèque.  
  
 L'assertion n'affecte le parcours de pile que si l'autorisation ayant fait l'objet de l'assertion et une autorisation demandée par un appelant en aval sont de même type, et si l'autorisation demandée est un sous-ensemble de l'autorisation ayant fait l'objet de l'assertion. Par exemple, si vous déclarez **FileIOPermission** pour lire tous les fichiers sur le lecteur C et une demande en aval est faite pour **FileIOPermission** pour lire les fichiers dans C:\Temp, l’assertion peut affecter le parcours de pile. Toutefois, si la demande était pour **FileIOPermission** pour écrire sur le lecteur C, l’assertion n’a aucun effet.  
  
 Pour effectuer des assertions, votre code doit disposer de l'autorisation faisant l'objet de l'assertion et de <xref:System.Security.Permissions.SecurityPermission>, qui représente le droit d'effectuer des assertions. Il est possible d'effectuer une assertion pour une autorisation qui n'a pas été octroyée à votre code. Toutefois, une telle assertion serait inutile puisque la vérification de sécurité échouerait avant même que l'assertion n'ait pu faire en sorte qu'elle réussisse.  
  
 L’illustration suivante montre ce qui se passe lorsque vous utilisez **Assert**. Supposons que les instructions suivantes soient vraies concernant les assemblys A, B, C, E et F, et les deux autorisations P1 et P1A :  
  
-   P1A représente le droit de lire les fichiers .txt présents sur le lecteur C.  
  
-   P1 représente le droit de lire tous les fichiers présents sur le lecteur C.  
  
-   P1A et P1 sont tous deux **FileIOPermission** types et P1A est un sous-ensemble de P1.  
  
-   Les assemblys E et F ont reçu l'autorisation P1A.  
  
-   L'assembly C a reçu l'autorisation P1.  
  
-   Les assemblys A et B n'ont reçu ni l'autorisation P1 ni l'autorisation P1A.  
  
-   La méthode A est contenue dans l'assembly A, la méthode B dans l'assembly B, et ainsi de suite.  
  
 ![](../../../docs/framework/misc/media/assert.gif "Assert")  
Utilisation de l'instruction Assert  
  
 Dans ce scénario de méthode A appelle B, B appelle C, C appelle E et E appelle F. méthode C déclare l’autorisation de lire des fichiers sur le lecteur C (autorisation P1) et la méthode E demande l’autorisation de lire les fichiers .txt sur le lecteur C (autorisation P1A). Lorsque la demande dans F est trouvée au moment de l’exécution, un parcours de pile est effectué afin de vérifier les autorisations de tous les appelants de F, en commençant par E. E a autorisation P1A, le parcours de pile se poursuit pour examiner les autorisations de C, où l’assertion de C est trouvée. Étant donné que l'autorisation demandée (P1A) est un sous-ensemble de l'autorisation ayant fait l'objet de l'assertion (P1), le parcours de pile s'arrête et la vérification de sécurité réussit automatiquement. Il n'est pas important que les assemblys A et B ne disposent pas de l'autorisation P1A. En procédant à l'assertion de P1, la méthode C garantit que ses appelants puissent accéder à la ressource protégée par P1, même s'ils n'ont pas reçu l'autorisation d'y accéder.  
  
 Si vous concevez une bibliothèque de classes et si une classe accède à une ressource protégée, vous devez, dans la plupart des cas, effectuer une demande de sécurité exigeant que les appelants de la classe possèdent l'autorisation appropriée. Si la classe effectue ensuite une opération pour dont vous savez que la plupart de ses appelants n’auront pas les autorisations, et si vous êtes prêt à prendre la responsabilité de laisser ces appelants appeler votre code, vous pouvez déclarer l’autorisation en appelant le **Assert** méthode sur un objet d’autorisation qui représente l’opération que le code fonctionne. À l’aide de **Assert** de cette façon permet aux appelants qui normalement n’a pas appeler votre code. Par conséquent, si vous procédez à l'assertion d'une autorisation, soyez sûr d'effectuer au préalable les vérifications de sécurité appropriées pour empêcher une utilisation abusive de votre composant.  
  
 Supposons, par exemple, que votre classe de bibliothèque hautement approuvée possède une méthode qui supprime les fichiers. Elle accède au fichier en appelant une fonction Win32 non managée. Un appelant appelle de votre code **supprimer** méthode, en passant le nom du fichier à supprimer, C:\Test.txt. Dans le **supprimer** (méthode), votre code crée un <xref:System.Security.Permissions.FileIOPermission> objet représentant l’accès en écriture à C:\Test.txt. (l'accès en écriture est nécessaire pour supprimer un fichier). Votre code appelle alors une vérification de sécurité impérative en appelant le **FileIOPermission** l’objet **à la demande** (méthode). Si l'un des appelants de la pile des appels n'a pas cette autorisation, une <xref:System.Security.SecurityException> est levée. Si aucune exception n'est levée, vous savez que tous les appelants ont le droit d'accéder à C:\Test.txt. Étant donné que vous pensez que la plupart de vos appelants n’auront pas l’autorisation d’accéder au code non managé, votre code crée ensuite un <xref:System.Security.Permissions.SecurityPermission> objet qui représente le droit d’appeler du code non managé et appelle l’objet **Assert** (méthode). Enfin, il appelle la fonction non managée Win32 pour supprimer C:\Text.txt, puis retourne le contrôle à l'appelant.  
  
> [!CAUTION]
>  Vous devez être sûr que votre code n'utilise pas d'assertions s'il peut être utilisé par un autre code pour accéder à une ressource protégée par l'autorisation faisant l'objet de l'assertion. Par exemple, dans le code qui écrit dans un fichier dont le nom est spécifié par l’appelant en tant que paramètre, vous ne devez pas déclarer le **FileIOPermission** pour écrire dans des fichiers, car votre code sera utilisation abusive par un tiers.  
  
 Quand vous utilisez la syntaxe de sécurité impérative, l’appel du **Assert** méthode sur plusieurs autorisations dans la même méthode provoque la levée d’une exception de sécurité. Au lieu de cela, vous devez créer un **PermissionSet** de l’objet, lui passer les autorisations individuelles que vous souhaitez appeler, puis appelez le **Assert** méthode sur le **PermissionSet** objet. Vous pouvez appeler la **Assert** méthode plusieurs fois lorsque vous utilisez la syntaxe de la sécurité déclarative.  
  
 L’exemple suivant illustre la syntaxe déclarative à des vérifications de sécurité à l’aide de la **Assert** (méthode). Notez que la **FileIOPermissionAttribute** syntaxe prend deux valeurs : une <xref:System.Security.Permissions.SecurityAction> énumération et l’emplacement du fichier ou du répertoire auquel l’autorisation est accordée. L’appel à **Assert** demandes d’accès à `C:\Log.txt` réussisse, même si les appelants ne sont pas vérifiées pour l’autorisation d’accès au fichier.  
  
```vb  
Option Explicit  
Option Strict  
  
Imports System  
Imports System.IO  
Imports System.Security.Permissions  
  
Namespace LogUtil  
   Public Class Log  
      Public Sub New()  
  
      End Sub  
  
     <FileIOPermission(SecurityAction.Assert, All := "C:\Log.txt")> Public Sub   
      MakeLog()  
         Dim TextStream As New StreamWriter("C:\Log.txt")  
         TextStream.WriteLine("This  Log was created on {0}", DateTime.Now) '  
         TextStream.Close()  
      End Sub  
   End Class  
End Namespace  
```  
  
```csharp  
namespace LogUtil  
{  
   using System;  
   using System.IO;  
   using System.Security.Permissions;  
  
   public class Log  
   {  
      public Log()  
      {      
      }     
      [FileIOPermission(SecurityAction.Assert, All = @"C:\Log.txt")]  
      public void MakeLog()  
      {     
         StreamWriter TextStream = new StreamWriter(@"C:\Log.txt");  
         TextStream.WriteLine("This  Log was created on {0}", DateTime.Now);  
         TextStream.Close();  
      }  
   }  
}   
```  
  
 Les fragments de code suivants illustrent la syntaxe impérative à des vérifications de sécurité à l’aide de la **Assert** (méthode). Dans cet exemple, une instance de la **FileIOPermission** objet est déclaré. Est passé à son constructeur **FileIOPermissionAccess.AllAccess** pour définir le type d’accès autorisé, suivi d’une chaîne décrivant l’emplacement du fichier. Une fois la **FileIOPermission** objet est défini, vous devez uniquement appeler son **Assert** méthode à substituer la vérification de sécurité.  
  
```vb  
Option Explicit  
Option Strict  
Imports System  
Imports System.IO  
Imports System.Security.Permissions  
Namespace LogUtil  
   Public Class Log  
      Public Sub New()  
      End Sub 'New  
  
      Public Sub MakeLog()  
         Dim FilePermission As New FileIOPermission(FileIOPermissionAccess.AllAccess, "C:\Log.txt")  
         FilePermission.Assert()  
         Dim TextStream As New StreamWriter("C:\Log.txt")  
         TextStream.WriteLine("This  Log was created on {0}", DateTime.Now)  
         TextStream.Close()  
      End Sub  
   End Class  
End Namespace  
```  
  
```csharp  
namespace LogUtil  
{  
   using System;  
   using System.IO;  
   using System.Security.Permissions;  
  
   public class Log  
   {  
      public Log()  
      {      
      }     
      public void MakeLog()  
      {  
         FileIOPermission FilePermission = new FileIOPermission(FileIOPermissionAccess.AllAccess,@"C:\Log.txt");   
         FilePermission.Assert();  
         StreamWriter TextStream = new StreamWriter(@"C:\Log.txt");  
         TextStream.WriteLine("This  Log was created on {0}", DateTime.Now);  
         TextStream.Close();  
      }  
   }  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Security.PermissionSet>  
 <xref:System.Security.Permissions.SecurityPermission>  
 <xref:System.Security.Permissions.FileIOPermission>  
 <xref:System.Security.Permissions.SecurityAction>  
 [Attributs](../../../docs/standard/attributes/index.md)  
 [Sécurité d’accès du code](../../../docs/framework/misc/code-access-security.md)
