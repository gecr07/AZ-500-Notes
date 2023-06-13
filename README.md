# AZ-500-Notes

# Explore Azure Active Directory features

> Azure Active Directory (Azure AD) is a cloud-based identity and access management service. This service helps employees access external resources, such as Microsoft 365, the Azure portal, and thousands of other software-as-a-service (SaaS) applications. Azure Active Directory also helps them access internal resources like apps on your corporate intranet network, along with any cloud apps developed for your organization. 


## What are the Azure AD licenses?

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/23ebde66-b85f-42f0-b62f-92e6fa1b222a)

Although the three Active Directory-based identity solutions share a common name and technology, they're designed to provide services that meet different customer demands. At a high level, these identity solutions and feature sets are:



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





