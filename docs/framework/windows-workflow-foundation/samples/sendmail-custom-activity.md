---
title: "Activité personnalisée SendMail"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 947a9ae6-379c-43a3-9cd5-87f573a5739f
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4fb8454d3e1e679154bc016e37b83c3ac4ff6768
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="sendmail-custom-activity"></a><span data-ttu-id="bd89e-102">Activité personnalisée SendMail</span><span class="sxs-lookup"><span data-stu-id="bd89e-102">SendMail Custom Activity</span></span>
<span data-ttu-id="bd89e-103">Cet exemple montre comment créer une activité personnalisée dérivée de <xref:System.Activities.AsyncCodeActivity> pour envoyer du courrier à l'aide de SMTP afin de l'utiliser dans une application de workflow.</span><span class="sxs-lookup"><span data-stu-id="bd89e-103">This sample demonstrates how to create a custom activity that derives from <xref:System.Activities.AsyncCodeActivity> to send mail using SMTP for use within a workflow application.</span></span> <span data-ttu-id="bd89e-104">L'activité personnalisée utilise les fonctionnalités de <xref:System.Net.Mail.SmtpClient> pour envoyer du courrier électronique de façon asynchrone et envoyer du courrier avec authentification.</span><span class="sxs-lookup"><span data-stu-id="bd89e-104">The custom activity uses the capabilities of <xref:System.Net.Mail.SmtpClient> to send e-mail asynchronously and to send mail with authentication.</span></span> <span data-ttu-id="bd89e-105">Elle fournit aussi certaines fonctionnalités d'utilisateur final telles que le mode Test, le remplacement des jetons, les modèles de fichier et le chemin d'accès de dépôt de test.</span><span class="sxs-lookup"><span data-stu-id="bd89e-105">It also provides some end-user features like test mode, token replacement, file templates, and test drop path.</span></span>  
  
 <span data-ttu-id="bd89e-106">Le tableau suivant décrit en détail les arguments pour l'activité `SendMail`.</span><span class="sxs-lookup"><span data-stu-id="bd89e-106">The following table details the arguments for the `SendMail` activity.</span></span>  
  
|<span data-ttu-id="bd89e-107">Nom</span><span class="sxs-lookup"><span data-stu-id="bd89e-107">Name</span></span>|<span data-ttu-id="bd89e-108">Type</span><span class="sxs-lookup"><span data-stu-id="bd89e-108">Type</span></span>|<span data-ttu-id="bd89e-109">Description</span><span class="sxs-lookup"><span data-stu-id="bd89e-109">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="bd89e-110">Host</span><span class="sxs-lookup"><span data-stu-id="bd89e-110">Host</span></span>|<span data-ttu-id="bd89e-111">Chaîne</span><span class="sxs-lookup"><span data-stu-id="bd89e-111">String</span></span>|<span data-ttu-id="bd89e-112">Adresse du serveur hôte SMTP.</span><span class="sxs-lookup"><span data-stu-id="bd89e-112">Address of the SMTP server host.</span></span>|  
|<span data-ttu-id="bd89e-113">Port</span><span class="sxs-lookup"><span data-stu-id="bd89e-113">Port</span></span>|<span data-ttu-id="bd89e-114">Chaîne</span><span class="sxs-lookup"><span data-stu-id="bd89e-114">String</span></span>|<span data-ttu-id="bd89e-115">Port du service SMTP dans l'hôte.</span><span class="sxs-lookup"><span data-stu-id="bd89e-115">Port of the SMTP service in the host.</span></span>|  
|<span data-ttu-id="bd89e-116">EnableSsl</span><span class="sxs-lookup"><span data-stu-id="bd89e-116">EnableSsl</span></span>|<span data-ttu-id="bd89e-117">bool</span><span class="sxs-lookup"><span data-stu-id="bd89e-117">bool</span></span>|<span data-ttu-id="bd89e-118">Indique si <xref:System.Net.Mail.SmtpClient> utilise le protocole SSL (Secure Sockets Layer) pour chiffrer la connexion.</span><span class="sxs-lookup"><span data-stu-id="bd89e-118">Specifies whether the <xref:System.Net.Mail.SmtpClient> uses Secure Sockets Layer (SSL) to encrypt the connection.</span></span>|  
|<span data-ttu-id="bd89e-119">UserName</span><span class="sxs-lookup"><span data-stu-id="bd89e-119">UserName</span></span>|<span data-ttu-id="bd89e-120">Chaîne</span><span class="sxs-lookup"><span data-stu-id="bd89e-120">String</span></span>|<span data-ttu-id="bd89e-121">Nom d'utilisateur pour définir les informations d'identification utilisées pour authentifier la propriété <xref:System.Net.Mail.SmtpClient.Credentials%2A> de l'expéditeur.</span><span class="sxs-lookup"><span data-stu-id="bd89e-121">Username to set up the credentials to authenticate the sender <xref:System.Net.Mail.SmtpClient.Credentials%2A> property.</span></span>|  
|<span data-ttu-id="bd89e-122">Mot de passe</span><span class="sxs-lookup"><span data-stu-id="bd89e-122">Password</span></span>|<span data-ttu-id="bd89e-123">Chaîne</span><span class="sxs-lookup"><span data-stu-id="bd89e-123">String</span></span>|<span data-ttu-id="bd89e-124">Mot de passe pour définir les informations d'identification utilisées pour authentifier la propriété <xref:System.Net.Mail.SmtpClient.Credentials%2A> de l'expéditeur.</span><span class="sxs-lookup"><span data-stu-id="bd89e-124">Password to set up the credentials to authenticate the sender <xref:System.Net.Mail.SmtpClient.Credentials%2A> property.</span></span>|  
|<span data-ttu-id="bd89e-125">Objet</span><span class="sxs-lookup"><span data-stu-id="bd89e-125">Subject</span></span>|<span data-ttu-id="bd89e-126"><xref:System.Activities.InArgument%601>\<chaîne ></span><span class="sxs-lookup"><span data-stu-id="bd89e-126"><xref:System.Activities.InArgument%601>\<string></span></span>|<span data-ttu-id="bd89e-127">Sujet du message.</span><span class="sxs-lookup"><span data-stu-id="bd89e-127">Subject of the message.</span></span>|  
|<span data-ttu-id="bd89e-128">Corps</span><span class="sxs-lookup"><span data-stu-id="bd89e-128">Body</span></span>|<span data-ttu-id="bd89e-129"><xref:System.Activities.InArgument%601>\<chaîne ></span><span class="sxs-lookup"><span data-stu-id="bd89e-129"><xref:System.Activities.InArgument%601>\<string></span></span>|<span data-ttu-id="bd89e-130">Corps du message.</span><span class="sxs-lookup"><span data-stu-id="bd89e-130">Body of the message.</span></span>|  
|<span data-ttu-id="bd89e-131">Pièces jointes</span><span class="sxs-lookup"><span data-stu-id="bd89e-131">Attachments</span></span>|<span data-ttu-id="bd89e-132"><xref:System.Activities.InArgument%601>\<chaîne ></span><span class="sxs-lookup"><span data-stu-id="bd89e-132"><xref:System.Activities.InArgument%601>\<string></span></span>|<span data-ttu-id="bd89e-133">Collection de pièces jointes utilisée pour stocker des données jointes à ce message électronique.</span><span class="sxs-lookup"><span data-stu-id="bd89e-133">Attachment collection used to store data attached to this e-mail message.</span></span>|  
|<span data-ttu-id="bd89e-134">From</span><span class="sxs-lookup"><span data-stu-id="bd89e-134">From</span></span>|<xref:System.Net.Mail.MailAddress>|<span data-ttu-id="bd89e-135">Adresse d'origine de ce message électronique.</span><span class="sxs-lookup"><span data-stu-id="bd89e-135">From address for this e-mail message.</span></span>|  
|<span data-ttu-id="bd89e-136">À</span><span class="sxs-lookup"><span data-stu-id="bd89e-136">To</span></span>|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|<span data-ttu-id="bd89e-137">Collection d’adresses qui contient les destinataires de ce message électronique.</span><span class="sxs-lookup"><span data-stu-id="bd89e-137">Address collection that contains the recipients of this e-mail message.</span></span>|  
|<span data-ttu-id="bd89e-138">CC</span><span class="sxs-lookup"><span data-stu-id="bd89e-138">CC</span></span>|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|<span data-ttu-id="bd89e-139">Collection d’adresses qui contient les destinataires de copie carbone (CC) pour ce message électronique.</span><span class="sxs-lookup"><span data-stu-id="bd89e-139">Address collection that contains the carbon copy (CC) recipients for this e-mail message.</span></span>|  
|<span data-ttu-id="bd89e-140">BCC</span><span class="sxs-lookup"><span data-stu-id="bd89e-140">BCC</span></span>|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|<span data-ttu-id="bd89e-141">Collection d’adresses qui contient les destinataires de copie carbone invisible (CCI) pour ce message électronique.</span><span class="sxs-lookup"><span data-stu-id="bd89e-141">Address collection that contains the blind carbon copy (BCC) recipients for this e-mail message.</span></span>|  
|<span data-ttu-id="bd89e-142">jetons</span><span class="sxs-lookup"><span data-stu-id="bd89e-142">Tokens</span></span>|<span data-ttu-id="bd89e-143"><xref:System.Activities.InArgument%601>< IDictionary\<chaîne, chaîne >></span><span class="sxs-lookup"><span data-stu-id="bd89e-143"><xref:System.Activities.InArgument%601><IDictionary\<string, string>></span></span>|<span data-ttu-id="bd89e-144">Jetons à remplacer dans le corps.</span><span class="sxs-lookup"><span data-stu-id="bd89e-144">Tokens to replace in the body.</span></span> <span data-ttu-id="bd89e-145">Cette fonctionnalité permet aux utilisateurs de spécifier certaines valeurs dans le corps qui peuvent être remplacées ultérieurement par les jetons fournis à l'aide de cette propriété.</span><span class="sxs-lookup"><span data-stu-id="bd89e-145">This feature allows users to specify some values in the body than can be replaced later by the tokens provided using this property.</span></span>|  
|<span data-ttu-id="bd89e-146">BodyTemplateFilePath</span><span class="sxs-lookup"><span data-stu-id="bd89e-146">BodyTemplateFilePath</span></span>|<span data-ttu-id="bd89e-147">Chaîne</span><span class="sxs-lookup"><span data-stu-id="bd89e-147">String</span></span>|<span data-ttu-id="bd89e-148">Chemin d'accès à un modèle de corps.</span><span class="sxs-lookup"><span data-stu-id="bd89e-148">Path of a template for the body.</span></span> <span data-ttu-id="bd89e-149">L'activité `SendMail` copie le contenu de ce fichier dans sa propriété de corps.</span><span class="sxs-lookup"><span data-stu-id="bd89e-149">The `SendMail` activity copies the contents of this file to its body property.</span></span><br /><br /> <span data-ttu-id="bd89e-150">Ce modèle peut contenir des jetons qui sont remplacés par le contenu de la propriété des jetons.</span><span class="sxs-lookup"><span data-stu-id="bd89e-150">The template can contain tokens that are replaced by the contents of the tokens property.</span></span>|  
|<span data-ttu-id="bd89e-151">TestMailTo</span><span class="sxs-lookup"><span data-stu-id="bd89e-151">TestMailTo</span></span>|<xref:System.Net.Mail.MailAddress>|<span data-ttu-id="bd89e-152">Lorsque cette propriété est définie, tous les courriers électroniques sont envoyés à l'adresse qu'elle indique.</span><span class="sxs-lookup"><span data-stu-id="bd89e-152">When this property is set, all e-mails are sent to the address specified in it.</span></span><br /><br /> <span data-ttu-id="bd89e-153">Cette propriété n'est pas conçue pour une utilisation lors du test des workflows.</span><span class="sxs-lookup"><span data-stu-id="bd89e-153">This property is intended to be used when testing workflows.</span></span> <span data-ttu-id="bd89e-154">Par exemple, assurez-vous que tous les courriers électroniques sont envoyés sans les envoyer aux destinataires réels.</span><span class="sxs-lookup"><span data-stu-id="bd89e-154">For example, when you want to make sure that all e-mails are sent without sending them to the actual recipients.</span></span>|  
|<span data-ttu-id="bd89e-155">TestDropPath</span><span class="sxs-lookup"><span data-stu-id="bd89e-155">TestDropPath</span></span>|<span data-ttu-id="bd89e-156">Chaîne</span><span class="sxs-lookup"><span data-stu-id="bd89e-156">String</span></span>|<span data-ttu-id="bd89e-157">Lorsque cette propriété est définie, tous les courriers électroniques sont également enregistrés dans le fichier indiqué.</span><span class="sxs-lookup"><span data-stu-id="bd89e-157">When this property is set, all e-mails are also saved in the specified file.</span></span><br /><br /> <span data-ttu-id="bd89e-158">Cette propriété est conçue pour une utilisation lors du test ou débogage des workflows, pour vérifier que le format et le contenu des messages électroniques sortants sont appropriés.</span><span class="sxs-lookup"><span data-stu-id="bd89e-158">This property is intended to be used when you are testing or debugging workflows, to make sure that the format and contents of the outgoing e-mails is appropriate.</span></span>|  
  
## <a name="solution-contents"></a><span data-ttu-id="bd89e-159">Contenu de la solution</span><span class="sxs-lookup"><span data-stu-id="bd89e-159">Solution Contents</span></span>  
 <span data-ttu-id="bd89e-160">La solution contient deux projets.</span><span class="sxs-lookup"><span data-stu-id="bd89e-160">The solution contains two projects.</span></span>  
  
|<span data-ttu-id="bd89e-161">Project</span><span class="sxs-lookup"><span data-stu-id="bd89e-161">Project</span></span>|<span data-ttu-id="bd89e-162">Description</span><span class="sxs-lookup"><span data-stu-id="bd89e-162">Description</span></span>|<span data-ttu-id="bd89e-163">Fichiers importants</span><span class="sxs-lookup"><span data-stu-id="bd89e-163">Important Files</span></span>|  
|-------------|-----------------|---------------------|  
|<span data-ttu-id="bd89e-164">SendMail</span><span class="sxs-lookup"><span data-stu-id="bd89e-164">SendMail</span></span>|<span data-ttu-id="bd89e-165">Activité SendMail</span><span class="sxs-lookup"><span data-stu-id="bd89e-165">The SendMail activity</span></span>|<span data-ttu-id="bd89e-166">1.  SendMail.cs : implémentation pour l'activité principale</span><span class="sxs-lookup"><span data-stu-id="bd89e-166">1.  SendMail.cs: implementation for the main activity</span></span><br /><span data-ttu-id="bd89e-167">2.  SendMailDesigner.xaml et SendMailDesigner.xaml.cs : concepteur pour l'activité SendMail</span><span class="sxs-lookup"><span data-stu-id="bd89e-167">2.  SendMailDesigner.xaml and SendMailDesigner.xaml.cs: designer for the SendMail activity</span></span><br /><span data-ttu-id="bd89e-168">3.  MailTemplateBody.htm : modèle pour le message électronique à envoyer.</span><span class="sxs-lookup"><span data-stu-id="bd89e-168">3.  MailTemplateBody.htm: template for the email to be sent out.</span></span>|  
|<span data-ttu-id="bd89e-169">SendMailTestClient</span><span class="sxs-lookup"><span data-stu-id="bd89e-169">SendMailTestClient</span></span>|<span data-ttu-id="bd89e-170">Client pour tester l'activité SendMail.</span><span class="sxs-lookup"><span data-stu-id="bd89e-170">Client to test the SendMail activity.</span></span>  <span data-ttu-id="bd89e-171">Ce projet illustre deux façons d'appeler l'activité SendMail : déclarative et par programme.</span><span class="sxs-lookup"><span data-stu-id="bd89e-171">This project demonstrates two ways of invoking the SendMail activity: declaratively, and programmatically.</span></span>|<span data-ttu-id="bd89e-172">1.  Sequence1.xaml : workflow qui appelle l'activité SendMail.</span><span class="sxs-lookup"><span data-stu-id="bd89e-172">1.  Sequence1.xaml: workflow that invokes the SendMail activity.</span></span><br /><span data-ttu-id="bd89e-173">2.  Program.cs : appelle Sequence1 et crée par programmation un workflow qui utilise SendMail.</span><span class="sxs-lookup"><span data-stu-id="bd89e-173">2.  Program.cs: invokes Sequence1 and also creates a workflow programmatically that uses SendMail.</span></span>|  
  
## <a name="further-configuration-of-the-sendmail-activity"></a><span data-ttu-id="bd89e-174">Configuration supplémentaire de l'activité SendMail</span><span class="sxs-lookup"><span data-stu-id="bd89e-174">Further configuration of the SendMail activity</span></span>  
 <span data-ttu-id="bd89e-175">Bien qu'elle ne soit pas illustrée dans l'exemple, les utilisateurs peuvent effectuer une configuration supplémentaire de l'activité SendMail.</span><span class="sxs-lookup"><span data-stu-id="bd89e-175">Although not shown in the sample, users can perform addition configuration of the SendMail activity.</span></span> <span data-ttu-id="bd89e-176">Les trois sections suivantes montrent comment procéder.</span><span class="sxs-lookup"><span data-stu-id="bd89e-176">The next three sections demonstrate how this is done.</span></span>  
  
### <a name="sending-an-email-using-tokens-specified-in-the-body"></a><span data-ttu-id="bd89e-177">Envoi d'un message électronique à l'aide de jetons spécifiés dans le corps</span><span class="sxs-lookup"><span data-stu-id="bd89e-177">Sending an email using tokens specified in the body</span></span>  
 <span data-ttu-id="bd89e-178">Cet extrait de code montre comment envoyer un message électronique avec des jetons dans le corps.</span><span class="sxs-lookup"><span data-stu-id="bd89e-178">This code snippet demonstrates how you can send email with tokens in the body.</span></span> <span data-ttu-id="bd89e-179">Notez la façon dont les jetons sont fournis dans la propriété de corps.</span><span class="sxs-lookup"><span data-stu-id="bd89e-179">Notice how the tokens are provided in the body property.</span></span> <span data-ttu-id="bd89e-180">Les valeurs pour ces jetons sont fournies à la propriété de jetons.</span><span class="sxs-lookup"><span data-stu-id="bd89e-180">Values for those tokens are provided to the tokens property.</span></span>  
  
```html  
IDictionary<string, string> tokens = new Dictionary<string, string>();  
tokens.Add("@name", "John Doe");  
tokens.Add("@date", DateTime.Now.ToString());  
tokens.Add("@server", "localhost");  
  
new SendMail  
{  
    From = new LambdaValue<MailAddress>(ctx => new MailAddress("john.doe@contoso.com")),  
    To = new LambdaValue<MailAddressCollection>(  
                    ctx => new MailAddressCollection() { new MailAddress("someone@microsoft.com") }),  
    Subject = "Test email",  
    Body = "Hello @name. This is a test email sent from @server. Current date is @date",  
    Host = "localhost",  
    Port = 25,  
    Tokens = new LambdaValue<IDictionary<string, string>>(ctx => tokens)  
};  
```  
  
### <a name="sending-an-email-using-a-template"></a><span data-ttu-id="bd89e-181">Envoi d'un message électronique à l'aide d'un modèle</span><span class="sxs-lookup"><span data-stu-id="bd89e-181">Sending an email using a template</span></span>  
 <span data-ttu-id="bd89e-182">Cet extrait de code montre comment envoyer un message électronique à l'aide de jetons de modèle dans le corps.</span><span class="sxs-lookup"><span data-stu-id="bd89e-182">This snippet shows how to send an email using a template tokens in the body.</span></span> <span data-ttu-id="bd89e-183">Notez que lorsque vous définissez la propriété `BodyTemplateFilePath`, il n'est pas nécessaire de fournir la valeur pour la propriété Body (le contenu du modèle sera copié dans le corps).</span><span class="sxs-lookup"><span data-stu-id="bd89e-183">Notice that when setting the `BodyTemplateFilePath` property we don’t need to provide the value for Body property (the contents of the template file will be copied to the body).</span></span>  
  
```  
new SendMail  
{    
    From = new LambdaValue<MailAddress>(ctx => new MailAddress("john.doe@contoso.com")),  
    To = new LambdaValue<MailAddressCollection>(  
                    ctx => new MailAddressCollection() { new MailAddress("someone@microsoft.com") }),  
    Subject = "Test email",  
    Host = "localhost",  
    Port = 25,  
    Tokens = new LambdaValue<IDictionary<string, string>>(ctx => tokens),  
    BodyTemplateFilePath = @"..\..\..\SendMail\Templates\MailTemplateBody.htm",   
};  
```  
  
### <a name="sending-mails-in-testing-mode"></a><span data-ttu-id="bd89e-184">Envoi de messages électronique en mode Test</span><span class="sxs-lookup"><span data-stu-id="bd89e-184">Sending Mails in Testing Mode</span></span>  
 <span data-ttu-id="bd89e-185">Cet extrait de code montre comment définir les deux propriétés de tests : en définissant `TestMailTo` vers tous les messages seront envoyés à john.doe@contoso.con (sans tenir compte des valeurs de, Cc, Cci).</span><span class="sxs-lookup"><span data-stu-id="bd89e-185">This code snippet shows how to set the two testing properties: by setting `TestMailTo` to all messages will be sent to john.doe@contoso.con (without regard of the values of To, Cc, Bcc).</span></span> <span data-ttu-id="bd89e-186">En définissant TestDropPath, tous les messages électroniques sortants seront aussi enregistrés dans le chemin d’accès fourni.</span><span class="sxs-lookup"><span data-stu-id="bd89e-186">By setting TestDropPath all outgoing emails will be also recorded in the provided path.</span></span> <span data-ttu-id="bd89e-187">Ces propriétés peuvent être définies indépendamment (elles ne sont pas liées).</span><span class="sxs-lookup"><span data-stu-id="bd89e-187">These properties can be set independently (they are not related).</span></span>  
  
```  
new SendMail  
{    
   From = new LambdaValue<MailAddress>(ctx => new MailAddress("john.doe@contoso.com")),  
   To = new LambdaValue<MailAddressCollection>(  
                    ctx => new MailAddressCollection() { new MailAddress("someone@microsoft.com") }),  
   Subject = "Test email",  
   Host = "localhost",  
   Port = 25,  
   Tokens = new LambdaValue<IDictionary<string, string>>(ctx => tokens),  
   BodyTemplateFilePath = @"..\..\..\SendMail\Templates\MailTemplateBody.htm",  
   TestMailTo= new LambdaValue<MailAddress>(ctx => new MailAddress("john.doe@contoso.com")),  
   TestDropPath = @"c:\Samples\SendMail\TestDropPath\",  
};  
```  
  
## <a name="set-up-instructions"></a><span data-ttu-id="bd89e-188">Instructions d'installation</span><span class="sxs-lookup"><span data-stu-id="bd89e-188">Set-Up Instructions</span></span>  
 <span data-ttu-id="bd89e-189">Vous devez avoir accès à un serveur SMTP pour cet exemple.</span><span class="sxs-lookup"><span data-stu-id="bd89e-189">Access to a SMTP server is required for this sample.</span></span>  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="bd89e-190">configuration d’un serveur SMTP, consultez les liens suivants.</span><span class="sxs-lookup"><span data-stu-id="bd89e-190"> setting up a SMTP server, see the following links.</span></span>  
  
-   [<span data-ttu-id="bd89e-191">Microsoft Technet</span><span class="sxs-lookup"><span data-stu-id="bd89e-191">Microsoft Technet</span></span>](http://go.microsoft.com/fwlink/?LinkId=166060)  
  
-   [<span data-ttu-id="bd89e-192">Configuration du Service SMTP (IIS 6.0)</span><span class="sxs-lookup"><span data-stu-id="bd89e-192">Configuring the SMTP Service (IIS 6.0)</span></span>](http://go.microsoft.com/fwlink/?LinkId=150456)  
  
-   [<span data-ttu-id="bd89e-193">IIS 7.0 : Configuration de courrier électronique SMTP</span><span class="sxs-lookup"><span data-stu-id="bd89e-193">IIS 7.0: Configure SMTP E-Mail</span></span>](http://go.microsoft.com/fwlink/?LinkId=150457)  
  
-   [<span data-ttu-id="bd89e-194">Comment installer le Service SMTP</span><span class="sxs-lookup"><span data-stu-id="bd89e-194">How to Install the SMTP Service</span></span>](http://go.microsoft.com/fwlink/?LinkId=150458)  
  
 <span data-ttu-id="bd89e-195">Les émulateurs SMTP fournis par des tiers ne sont pas disponibles pour le téléchargement.</span><span class="sxs-lookup"><span data-stu-id="bd89e-195">SMTP emulators provided by third parties are available for download.</span></span>  
  
##### <a name="to-run-this-sample"></a><span data-ttu-id="bd89e-196">Pour exécuter cet exemple</span><span class="sxs-lookup"><span data-stu-id="bd89e-196">To run this sample</span></span>  
  
1.  <span data-ttu-id="bd89e-197">Dans [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], ouvrez le fichier solution SendMail.sln.</span><span class="sxs-lookup"><span data-stu-id="bd89e-197">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the SendMail.sln solution file.</span></span>  
  
2.  <span data-ttu-id="bd89e-198">Vérifiez que vous avez accès à un serveur SMTP valide.</span><span class="sxs-lookup"><span data-stu-id="bd89e-198">Ensure that you have access to a valid SMTP server.</span></span> <span data-ttu-id="bd89e-199">Consultez les instructions d'installation.</span><span class="sxs-lookup"><span data-stu-id="bd89e-199">See the set-up instructions.</span></span>  
  
3.  <span data-ttu-id="bd89e-200">Configurez le programme avec l'adresse de votre serveur et les adresses d'expéditeur et de destinataire.</span><span class="sxs-lookup"><span data-stu-id="bd89e-200">Configure the program with your server address, and From and To e-mail addresses.</span></span>  
  
     <span data-ttu-id="bd89e-201">Pour exécuter correctement cet exemple, vous devrez peut-être configurer la valeur des adresses d'expéditeur et de destinataire et l'adresse du serveur SMTP dans les fichiers  Program.cs et Sequence.xaml.</span><span class="sxs-lookup"><span data-stu-id="bd89e-201">To correctly run this sample, you may need to configure the value of From and To e-mail addresses and the address of the SMTP server in  Program.cs and in Sequence.xaml.</span></span> <span data-ttu-id="bd89e-202">Vous devrez modifier l'adresse à ces deux emplacements car le programme envoie les messages de différentes façons.</span><span class="sxs-lookup"><span data-stu-id="bd89e-202">You will need to change the address in both locations since the program sends mail in two different ways</span></span>  
  
4.  <span data-ttu-id="bd89e-203">Pour générer la solution, appuyez sur Ctrl+Maj+B.</span><span class="sxs-lookup"><span data-stu-id="bd89e-203">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
5.  <span data-ttu-id="bd89e-204">Pour exécuter la solution, appuyez sur Ctrl+F5.</span><span class="sxs-lookup"><span data-stu-id="bd89e-204">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="bd89e-205">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="bd89e-205">The samples may already be installed on your machine.</span></span> <span data-ttu-id="bd89e-206">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="bd89e-206">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="bd89e-207">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="bd89e-207">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="bd89e-208">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="bd89e-208">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\SendMail`