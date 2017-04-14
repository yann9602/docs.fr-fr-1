---
title: "Informations syst&#232;me et Windows Forms | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "noms de domaines, récupérer"
  - "informations système (Windows Forms)"
  - "SystemInformation (classe Windows Forms)"
  - "noms d'utilisateurs, récupérer"
ms.assetid: 30cf43a3-8cb2-4ff3-862b-6c34576616a8
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# Informations syst&#232;me et Windows Forms
Parfois, il est nécessaire de recueillir des informations au sujet de l'ordinateur sur lequel s'exécute votre application afin de prendre des décisions concernant votre code.  Par exemple, vous pouvez avoir une fonction qui est uniquement applicable lorsque l'ordinateur est connecté à un domaine de réseau particulier ; dans ce cas, vous devez trouver un moyen de déterminer le domaine et de désactiver la fonction si le domaine n'est pas présent.  
  
 Les applications Windows Forms peuvent utiliser la classe <xref:System.Windows.Forms.SystemInformation> pour déterminer un certain nombre de choses au sujet d'un ordinateur au moment de l'exécution.  L'exemple suivant montre comment utiliser la classe <xref:System.Windows.Forms.SystemInformation> pour récupérer le nom de l'utilisateur \(<xref:System.Windows.Forms.SystemInformation.UserName%2A>\) et le nom du domaine \(<xref:System.Windows.Forms.SystemInformation.UserDomainName%2A>\) :  
  
```vb  
Dim User As String = Windows.Forms.SystemInformation.UserName  
Dim Domain As String = Windows.Forms.SystemInformation.UserDomainName  
  
MessageBox.Show("Good morning " & User & ". You are connected to " _  
& Domain)  
  
```  
  
```csharp  
string User = SystemInformation.UserName;  
string Domain = SystemInformation.UserDomainName;  
  
MessageBox.Show("Good morning " + User + ". You are connected to " _  
+ Domain)  
```  
  
 Tous les membres de la classe <xref:System.Windows.Forms.SystemInformation> sont en lecture seule ; vous ne pouvez pas modifier les paramètres d'un utilisateur.  La classe, qui comprend plus de 100 membres, peut retourner des informations allant du nombre d'écrans connectés à l'ordinateur \(<xref:System.Windows.Forms.SystemInformation.MonitorCount%2A>\) à l'espacement des icônes dans l'Explorateur Windows \(<xref:System.Windows.Forms.SystemInformation.IconHorizontalSpacing%2A> et <xref:System.Windows.Forms.SystemInformation.IconVerticalSpacing%2A>\).  
  
 <xref:System.Windows.Forms.SystemInformation.ComputerName%2A>, <xref:System.Windows.Forms.SystemInformation.DbcsEnabled%2A>, <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A> et <xref:System.Windows.Forms.SystemInformation.TerminalServerSession%2A> comptent parmi les membres les plus utiles de la classe <xref:System.Windows.Forms.SystemInformation>.  
  
## Voir aussi  
 <xref:System.Windows.Forms.SystemInformation>   
 [Gestion de l'alimentation dans Windows Forms](../../../../docs/framework/winforms/advanced/power-management-in-windows-forms.md)