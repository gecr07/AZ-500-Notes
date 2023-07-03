# AZ-500-Notes

# Explore Azure Active Directory features

> Azure Active Directory (Azure AD) is a cloud-based identity and access management service. This service helps employees access external resources, such as Microsoft 365, the Azure portal, and thousands of other software-as-a-service (SaaS) applications. Azure Active Directory also helps them access internal resources like apps on your corporate intranet network, along with any cloud apps developed for your organization. 


## What are the Azure AD licenses?

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/23ebde66-b85f-42f0-b62f-92e6fa1b222a)

Although the three Active Directory-based identity solutions share a common name and technology, they're designed to provide services that meet different customer demands. At a high level, these identity solutions and feature sets are:


## No actions en un JSON de permisos

Esto lo que hace es sacar acciones cuando se usa un *.

## Deny 

Esto es ya bloquear todas las acciones que se definan en deny. Ademas al parecer deny tiene prioridad.
## Self-managed Active Directory Domain Services



## Azure Active Directory (Azure AD )

Azure Active Directory (Azure AD) - Cloud-based identity and mobile device management that provides user account and authentication services for resources such as Microsoft 365, the Azure portal, or SaaS applications.
Azure AD can be synchronized with an on-premises AD DS environment to provide a single identity to users that works natively in the cloud.


## Managed Azure Active Directory Domain Services



## Active Directory Domain Services (AD DS) 

Enterprise-ready lightweight directory access protocol (LDAP) server that provides key features such as identity and authentication, computer object management, group policy, and trusts.
AD DS is a central component in many organizations with an on-premises IT environment and provides core user account authentication and computer management features

## Azure Active Directory Domain Services (Azure AD DS) 

Provides managed domain services with a subset of fully compatible traditional AD DS features such as domain join, group policy, LDAP, and Kerberos / New Technology LAN Manager (NTLM) authentication.
Azure AD DS integrates with Azure AD, which can synchronize with an on-premises AD DS environment. This ability extends central identity use cases to traditional web applications that run in Azure as part of a lift-and-shift strategy. 

### Azure AD DS and self-managed AD DS

If you have applications and services that need access to traditional authentication mechanisms such as Kerberos or NTLM, there are two ways to provide Active Directory Domain Services in the cloud:

-A managed domain that you create using Azure Active Directory Domain Services (Azure AD DS). Microsoft creates and manages the required resources.

-A self-managed domain that you create and configure using traditional resources such as virtual machines (VMs), Windows Server guest OS, and Active Directory Domain Services (AD DS). You then continue to administer these resources.


Los modelos de implementación comunes para un entorno de AD DS autoadministrado que proporciona identidad a las aplicaciones y servicios en la nube incluyen los siguientes:


Standalone cloud-only AD DS - Azure VMs are configured as domain controllers, and a separate, cloud-only AD DS environment is created. This AD DS environment doesn't integrate with an on-premises AD DS environment. A different set of credentials is used to sign in and administer VMs in the cloud.

Resource forest deployment - Azure VMs are configured as domain controllers, and an AD DS domain that's part of an existing forest is created. A trust relationship is then configured to an on-premises AD DS environment. Other Azure VMs can domain-join this resource forest in the cloud. User authentication runs over a VPN / ExpressRoute connection to the on-premises AD DS environment.

Extend on-premises domain to Azure - An Azure virtual network connects to an on-premises network using a VPN / ExpressRoute connection. Azure VMs connect to this Azure virtual network, which lets them domain-join to the on-premises AD DS environment.

An alternative is to create Azure VMs and promote them as replica domain controllers from the on-premises AD DS domain. These domain controllers replicate over a VPN / ExpressRoute connection to the on-premises AD DS environment. The on-premises AD DS domain is effectively extended into Azure.


## Investigate roles in Azure AD


Azure AD-specific roles: These roles grant permissions to manage resources within Azure AD only. For example, User Administrator, Application Administrator, and Groups Administrator all grant permissions to manage resources that live in Azure AD.

Service-specific roles: For major Microsoft 365 services (non-Azure AD), we have built service-specific roles that grant permissions to manage all features within the service. For example, Exchange Administrator, Intune Administrator, SharePoint Administrator, and Teams Administrator roles can manage features with their respective services. Exchange Administrator can manage mailboxes, Intune Administrator can manage device policies, SharePoint Administrator can manage site collections, Teams Administrator can manage call qualities, and so on.

Cross-service roles: There are some roles that span services. We have two global roles - Global Administrator and Global Reader. All Microsoft 365 services honor these two roles. Also, there are some security-related roles like Security Administrator and Security Reader that grant access across multiple security services within Microsoft 365. For example, using Security Administrator roles in Azure AD, you can manage Microsoft 365 Defender portal, Microsoft Defender Advanced Threat Protection, and Microsoft Defender for Cloud Apps. Similarly, in the Compliance Administrator role, you can manage Compliance-related settings in the Compliance portal, Exchange, and so on.

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/6d502c49-fb84-4a32-a107-681755f34ea0)

Son muchos roles( que ya conoces)

> https://learn.microsoft.com/en-us/training/modules/azure-active-directory/6-roles-azure-active-directory

## Características y ventajas de Azure AD DS

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/da98408d-5d9b-432f-bd5c-5f8064f09472)

***Add new users or delete existing users from your Azure Active Directory (Azure AD) tenant. To add or delete users, you must be a User Administrator or Global Administrator.***

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/179f36ee-bcb3-4717-b91f-ed695812af03)


> You can create a dynamic group for either devices or users but not for both. You can't create a device group based on the device owners' attributes. Device membership rules can only reference device attributions.

## Configure Azure AD administrative units

An administrative unit is an Azure AD resource that can be a container for other Azure AD resources. An administrative unit can contain only users and groups. Administrative units restrict permissions in a role to any portion of your organization that you define. You could, for example, use administrative units to delegate the Helpdesk Administrator role to regional support specialists, so they can manage users only in the region that they support.

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/1a1fc90e-26d1-4796-b8c5-8756425b6e71)

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/00a2cd45-1798-4b82-9fd4-7427bad75f77)

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/e095718a-4b2f-4250-9b98-cddf6e559eba)

# Implement Hybrid identity

## Deploy Azure AD connect

Azure AD Connect will integrate your on-premises directories with Azure Active Directory. This allows you to provide a common identity for your users for Microsoft 365, Azure, and SaaS applications integrated with Azure AD.

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/b379b92e-c651-44a2-b24b-923a4c508e12)


> Using AD Connect Health works by installing an agent on each of your on-premises sync servers.

> If you decide to use Federation with Active Directory Federation Services (AD FS), you can optionally set up password hash synchronization as a backup in case your AD FS infrastructure fails.

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/23325ab6-289d-474c-9198-780ff548e228)

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/3c5c9319-ed63-47b5-820d-604f82a4f00d)


# Deploy Azure AD identity protection

Azure Active Directory Identity Protection includes three default policies that administrators can choose to enable. These policies include limited customization but are applicable to most organizations. All the policies allow for excluding users such as your emergency access or break-glass administrator accounts.+

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/3be937c8-bd68-43b6-803d-c64ab69b6af9)

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/059855da-a675-4ce3-8cd1-1f399d438dfa)

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/ee27f486-725e-47be-ac17-f15c464a0c5b)

## Configure risk event detections

To protect your users, you can configure risk-based policies in Azure Active Directory (Azure AD) that automatically respond to risky behaviors. Azure AD Identity Protection policies can automatically block a sign-in attempt or require additional action, such as requiring a password change or prompt for Azure AD Multi-Factor Authentication. These policies work with existing Azure AD Conditional Access policies as an extra layer of protection for your organization. Users may never trigger a risky behavior in one of these policies, but your organization is protected if an attempt to compromise your security is made.

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/757f0eb6-9a47-4b71-8766-26fd15b94429)

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/4963037d-5be1-4ec2-9ae2-742372c21859)

## Client apps

Conditional Access policies by default apply to browser-based applications and applications that utilize modern authentication protocols. In addition to these applications, administrators can choose to include Exchange ActiveSync clients and other clients that utilize legacy protocols.

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/e21ed104-db15-4947-80a2-17d9fccf662e)

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/08d6341e-7d9c-402f-ad91-b2626069fd9c)


## Deploy multifactor authentication in Azure

Azure Active Directory Multi-Factor Authentication helps safeguard access to data and applications while maintaining simplicity for users. It provides additional security by requiring a second form of authentication and delivers strong authentication through a range of easy to use authentication methods.

For organizations that need to be compliant with industry standards, such as the Payment Card Industry (PCI) Data Security Standard (DSS) version 3.2, MFA is a must have capability to authenticate users. Beyond being compliant with industry standards, enforcing MFA to authenticate users can also help organizations to mitigate credential theft attacks.

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/250a7578-fc8a-44e7-9c08-9e02a773ad6b)

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/c1283056-5e71-4011-b773-3268b47d2ae3)

> The Trusted IPs bypass works only from inside of the company intranet. If you select the All Federated Users option and a user signs in from outside the company intranet, the user must authenticate by using two-step verification. The process is the same even if the user presents an AD FS claim.


## Enable multifactor authentication

To enable MFA, go to the User Properties in Azure Active Directory, and then the Multi-Factor Authentication option. From there, you can select the users that you want to modify and enable for MFA. You can also bulk enable groups of users with PowerShell. User's states can be Enabled, Enforced, or Disabled.

> Remember, you can only enable MFA for organizational accounts stored in Azure Active Directory. These are also called work or school accounts.

## Configure conditional access conditions

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/ac81df8b-aa4b-49d3-9a15-66d5b87ffd2d)

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/6b08318c-c702-4066-9b3c-c59a4e919400)

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/092a5dc0-db9e-430b-9ff2-85b83d285ce6)

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/c149067e-42fb-4c7c-ab24-3ce4bd3bcdbf)


# Preguntas de examen 

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/7426d5b5-fed6-46aa-809a-ade74827727f)

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/0e1ef9b1-4478-40b4-bbee-950228e28d7c)

## RISK levels

Investiga los risk level bien de la pagina de microsoft.

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/25c6d3e1-a0b2-442e-a18a-0fedb4612e27)

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/63ce7f77-0d68-4141-95f5-caf8dc22cf44)

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/c9525ca7-3389-4210-8840-c94b746091ae)


![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/99c32582-ad42-4b06-8219-385ed42af47f)

## AKS 

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/afef7919-05a2-45ce-afb7-dec707532a16)


The container network interface (CNI) plug-in is responsible for providing network connectivity to containers running on a host. Answer is correct.


![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/28fb7393-a734-4119-8111-a85f10363537)

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/c3f8b14f-e86e-4765-9712-0e5ef9cc1840)

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/b8c169a7-4442-4fa7-828a-c8273d167eb8)

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/ec351677-37cb-42d9-8e21-d86eed6dfe06)

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/f07eb0e0-4c5f-4d7f-a87b-fee983c4d3b8)

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/0b53ed63-95a4-454c-ab87-bc40e885aeab)

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/a52c0488-484e-430f-8b00-f5ac19bc777b)

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/eb2011bb-e74e-4fa3-b172-a49ecbb274a4)

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/f4264f95-8b28-4fe7-b1f2-3c35506530f2)

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/abcfd7a0-fe32-4117-8b8f-f65d3a643d70)

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/fa04675d-3c8c-4ef1-89bf-14be8d00ffc5)

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/a607ad49-4e8c-43f4-a367-00cab2fea389)

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/87a53281-a35e-49a4-b096-a7d6d46f2cfe)

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/e239f402-f887-4215-ada8-6192c5280c09)

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/dbe5cd4a-135e-417c-8d01-6f18b2ecab5f)

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/499c14cd-4da8-44a1-8a53-259a232f7af2)

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/211e32ad-da68-4b74-a080-acfb67f835b1)

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/a0a64958-f301-4992-8745-dd9656c4bc59)

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/699b4c26-28c5-43f0-8c0e-492fff705911)

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/2dddb413-f13b-496f-956b-f69cb7121e74)

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/5f53c4cc-0f70-407d-894f-abda6c726865)

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/70fdba1e-bc7e-49c1-8e68-ebf8f268e718)

# Explicacion de Tenant que esta arriba de subscription

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/4429910b-c2f1-4f3b-abe5-bc1da87cc0d4)

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/b5b5e14f-eea2-4cb1-bd96-6f12e03ac6b3)

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/b35bad9b-a825-443d-9761-69ca6375eeea)

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/be06f282-cab7-4619-b063-a4ccd89028cf)

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/c207c50f-55ec-4685-8d66-d2d7d32f81b2)

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/6d5d7d06-63a1-4f34-9b56-4946576c6743)

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/f57d8a13-1c99-4f97-9a6c-c0fe175a4a91)

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/0b7e8c54-7e7d-4fd3-a29d-190d7f552680)

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/e1d8125e-deca-4118-867a-03f61489cd5e)

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/58c8b50f-a529-4f8d-b0f9-3a39c093c677)

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/97f5427e-2f88-4e7c-8b16-6881cb913828)

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/449e3e45-4e8d-4114-b511-abd82c3ecf0b)

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/f1498380-e18c-4f39-82d0-03e75c7e616c)


## Azure HDInsight documentation

Azure HDInsight is a managed Apache Hadoop service that lets you run Apache Spark, Apache Hive, Apache Kafka, Apache HBase, and more in the cloud.

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/d41da77e-2b88-4ca9-bcda-b965a087f805)

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/206ba5ca-e837-4775-970b-e38cf272b817)

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/c5874bb2-add4-463f-a7cc-06a6dada26e2)

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/1972aad1-1c67-45b9-91d3-ea8813b455f1)

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/9bcf9274-2cd4-4505-a827-1e4bcbe255a8)

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/183b8ebd-b35a-4825-bec5-0c000d67ca26)

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/679fa51f-1698-4c37-a07f-e22eafa940cd)

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/c9223d22-619c-4bbd-9ce9-5ef7d5c8cd3b)

##  over service-level shared access signatures (SASs)

A stored access policy provides an additional level of control over service-level shared access signatures (SASs) on the server side. Establishing a stored access policy serves to group shared access signatures and to provide additional restrictions for signatures that are bound by the policy.

You can use a stored access policy to change the start time, expiry time, or permissions for a signature. You can also use a stored access policy to revoke a signature after it has been issued.

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/3e059a70-b318-4dd5-8c1c-ed461fbfe14f)

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/63d2383a-43e8-4153-b5a3-fc0c45c31234)

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/7c61e73e-d993-4608-b266-7c027ac3007d)

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/2fdd398d-96b0-4fad-bf74-c4986a5080e8)

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/0e6f5c30-bc50-4e3f-93ae-b1f788723799)



![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/089495d1-f135-4afb-b5b2-48c8359a15ac)

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/a1ffe7da-aace-478c-8315-38d13eca14ae)

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/d430f82a-cc66-479a-8e7f-7d98f7452f89)

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/d346da96-36c6-4269-9cc0-cc6395411bdf)

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/db7e699b-a18d-4113-9f20-7b46bb132f18)

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/dc007f6f-439c-4b50-9eaa-3510a647cc5d)


![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/ada0eccf-18ca-4769-9ce1-fa0dc5f3e959)


![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/8f3df2d2-77d6-4161-ba2e-49fbb6034007)


![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/f4278d97-d614-4afd-ac38-8b14f57e3a51)

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/0531001c-052a-4610-a31b-6cc165ffca9d)

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/9e04bb37-5480-4b62-a382-76274df10ab2)


## cloning resources


rsharma007 Highly Voted 1 year, 10 months ago
Built-in AD roles can't be cloned, but built-in subscription roles can be. Custom roles of either type can be cloned.

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/650c5438-e82b-428b-81a1-ed0c119b9fb6)

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/769d2375-662a-42be-9afe-172aed0d946a)

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/da04f3c4-1b5e-4ef5-b8c8-cdd6ac865aeb)

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/45369e76-53dd-4563-833f-068fc35d5b00)

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/703bcaf2-3aeb-4844-ac71-48c8f26a0f4c)

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/7aa0524f-bf44-4c74-b50e-6ff6763dfe79)

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/fc3da028-c91d-4e0b-b7e1-46092177fc4b)

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/f872f895-7f98-4630-a14e-d783e8203f8b)

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/09fe99e8-c5f7-4bfc-8d4f-6c848e1a7a6d)

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/4c3056a9-2351-4e44-af04-4549f0609030)

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/b74e607f-e2e6-4943-9a15-5dd9dde15d39)

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/1f3aa2a4-043e-4877-8360-0dba798dc648)

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/b79560c0-d17b-47b2-b0af-449cdb3231af)

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/8f0737ca-a532-4ef6-b9a4-3c9cc612b2f3)

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/81e47af1-663b-477e-ba11-269e91d7a589)


![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/7830e36e-8010-48b2-a33a-7519d69d98fb)


![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/93c08358-26b0-4f3a-9661-71d596b74710)


![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/62975c6f-9f27-42aa-afa9-59ac97802732)


![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/fa2ac237-92b1-4707-b9fa-cb1bc8ee2b83)


![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/53362101-71da-4da4-8037-e50341ac9ccf)


## There are three types of service principal(entidades principales de servicio):
- Application - The type of service principal is the local representation, or application instance, of a global application object in a single tenant or directory. 
- Managed identity - This type of service principal is used to represent a managed identity. Managed identities eliminate the need for developers to manage credentials. Managed identities provide an identity for applications to use when connecting to resources that support Azure AD authentication. 
- Legacy - This type of service principal represents a legacy app, which is an app created before app registrations were introduced or an app created through legacy experiences.


![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/62db80cf-d7e8-40aa-87c8-767c106b1bcf)


![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/794f8714-ed22-41a4-8408-f5381189f3b4)


![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/16482cb3-6415-4d9e-9587-a4f9b865997f)


## UPN 

¡Claro! El User Principal Name (UPN) es una forma de identificar de manera única a un usuario en un dominio de Active Directory. Generalmente, sigue el formato de "nombredeusuario@nombrededominiodelusuario". Aquí tienes un ejemplo de un User Principal Name:

-Nombre de usuario: juan.perez

-Nombre de dominio: ejemplo.com

Entonces, el User Principal Name (UPN) de ese usuario sería: juan.perez@ejemplo.com

De esta manera, el UPN proporciona una forma legible y fácil de recordar de identificar a un usuario en un dominio de Active Directory.

> "Deny assignments block users from performing specific actions even if a role assignment grants them access. At this time, the only way you can add your own deny assignments is by using Azure Blueprints."


![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/9d9827f9-0e9d-4feb-85a8-334c082c9372)


![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/c47ee68e-fa19-4de0-bd1a-ec0eaa54e99a)



![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/2e7f75ef-1520-4d88-b1ab-f55eae0fc357)


## App1 has service principal.
https://learn.microsoft.com/en-us/azure/active-directory/develop/howto-create-service-principal-portal

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/6d4e520d-2d56-4287-918d-1b4f93fff9ea)


![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/47e0bbe0-f60d-4270-aa12-ecefa90a5b4d)

## Azure Container Registry Content Trust


![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/a9063bd9-6c6e-4168-83f4-23c6d8a5895f)

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/bf512b10-73cc-4e82-9b07-c9923c086a06)

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/a10f1bb5-74c8-434f-9c99-1a2271d7dcd3)

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/23d450ac-69f5-4dbc-b242-0018b756d23e)

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/16228a69-469e-4632-965c-846b8928c60a)

## Azure Resource Manager

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/495954bb-62b2-493c-a098-9e825403b49c)

To implement infrastructure as code for your Azure solutions, use Azure Resource Manager templates (ARM templates). The template is a JavaScript Object Notation (JSON) file that defines the infrastructure and configuration for your project. The template uses declarative syntax, which lets you state what you intend to deploy without having to write the sequence of programming commands to create it. In the template, you specify the resources to deploy and the properties for those resources.

## Virtual Network service endpoints

Virtual Network (VNet) service endpoint provides secure and direct connectivity to Azure services over an optimized route over the Azure backbone network. Endpoints allow you to secure your critical Azure service resources to only your virtual networks. Service Endpoints enables private IP addresses in the VNet to reach the endpoint of an Azure service without needing a public IP address on the VNet.

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/0a09d79a-dfca-4e54-993c-8064de1ef245)

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/699dcc81-e2e1-4278-a9d7-ce671fbf55c1)

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/fb7b2ac6-4047-43a8-9153-718ac7bc38b3)

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/e42e352d-252b-4230-a358-ec9afc447dd6)

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/cbb88153-2c89-48ad-9183-7e957c544233)

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/532130e7-0dc0-40ed-9c5d-f8ec4280c68e)

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/99301477-a8f7-49f2-bdb2-06c06d496446)

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/012e60cc-5b59-4281-a15d-a8ac0b60b06f)

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/6401246b-faf5-4ddb-807f-818784ef3443)

## Locking resources 

Locking Mode applies to the blueprint assignment and it has three options: Don't Lock, Read Only, or Do Not Delete. The locking mode is configured during artifact deployment during a blueprint assignment. A different locking mode can be set by updating the blueprint assignment. Locking modes, however, can't be changed outside of Azure Blueprints.

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/fe20265e-de9c-4227-86db-e7e3939f096b)

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/5f4ea82f-9f3f-4cc0-b67d-bebffc3f7f4e)

## Container env variables 

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/f6d2d221-0ff6-485f-9a0e-f8858d46f5ca)

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/3ad13bc1-b198-4886-ba7c-b81c4f37f0ac)

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/26a355a9-9cf8-4ba4-9d0a-4b1b52d1ae1d)

> The service will detect where the temporary exceptions need to be created and act accordingly. The only requirement is that there IS an NSG either on the vmNIC or the subnet to which the required exceptions can be added as required. If there is no NSG then a warning is surfaced via Azure Security Center.
>

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/11293c06-5cf6-4fb3-9c0a-aa70c19e4453)


![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/339ee4f3-9e82-4c45-a4eb-2ed5de0d9c3f)

> Microsoft Defender for container registries has been deprecated. Now Microsoft Defender for Containers can check windows images too.

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/07367586-ea2b-4f21-bad4-75c2fe4c5f00)

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/1e184210-d0ac-49ce-8141-fbd8886fe0b7)

## Adaptive application controls

are an intelligent and automated solution for defining allowlists of known-safe applications for your machines.

Often, organizations have collections of machines that routinely run the same processes. Microsoft Defender for Cloud uses machine learning to analyze the applications running on your machines and create a list of the known-safe software. Allowlists are based on your specific Azure workloads, and you can further customize the recommendations using the following instructions.

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/ba87ff16-b7c3-42a1-9e3f-838372aed288)

## App Service documentation

Azure App Service enables you to build and host web apps, mobile back ends, and RESTful APIs in the programming language of your choice without managing infrastructure. It offers auto-scaling and high availability, supports both Windows and Linux, and enables automated deployments from GitHub, Azure DevOps, or any Git repo. Learn how to use Azure App Service with our quickstarts, tutorials, and samples.

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/7b7b9fbc-6def-49f8-8365-4d5841663d4c)

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/440bfe71-3d51-400a-a820-36bda5fdbcb3)


![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/4b0366af-013b-48a1-8143-9cbce7147dc9)


![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/ae4042b4-574c-46ff-9b6d-7173d5442c3c)


![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/1eb2858c-f624-4608-aff4-07fcada2392c)


![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/c39519d8-d50a-4aef-9183-827d5be35a08)


![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/8148d831-ab99-4872-9cd3-4dc359f9e240)

## Network Security Groups (NSG) vs. Application Security Groups (ASG)

> On the other side an application security group can be used within a network security group and its inbound and outbound security rules as source or destination. The application security group can be associated with a virtual machine and therefore you can group virtual machines and define network security policies based on those groups.

> https://blog.matrixpost.net/network-security-groups-nsg-vs-application-security-groups-asg/


![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/340a3324-1dfa-4eae-87a6-8d3d36b271db)


![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/b8449dec-a9a3-4ed7-af87-c0a35af77ac9)


![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/5d2eef87-4cd9-400e-8a4a-ef7b76613c44)


![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/16921f94-9eaa-45e3-a698-b64316de1983)


![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/69b21afb-a00a-488d-b7c0-c9d98fc1155f)

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/93e276e2-7896-4223-b804-08033aa012d2)


![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/c95f4356-4a60-4b72-b316-bee470ad39a5)

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/29485b73-bb59-4de3-99ac-45025434d4fe)

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/87dae6ec-8445-42b5-afaf-1ef385c84dda)

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/e107e936-9b1a-4149-8619-347ac3d5bc20)






