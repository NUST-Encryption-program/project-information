#<div align = center>githubʹ��ָ����</div>
===========================================

***

##github����

&emsp;&emsp;�����ǵ���Ŀ��Ҫ����Э����ʱ����һ�������Ĵ����ĵ��ֿ�ͻ�ܷ��㡣
���ڷ��������ţ�����ѡ��ʹ��github��

Github��һ���ṩ��Git����汾�������ķ�������ʹ�ð汾���ƺʹ����й���ʲô�ô��أ�

- &emsp;&emsp;���ǿ���ͨ��github����վ��ʱ�����������ǵĴ�����ĵ����ϣ��磺arduino-exercises����

- &emsp;&emsp;���ǿ��Ը��������ύ���������ĸ��ģ�Ҳ������������˻��¶����м�¼ :P ���磺arduino-exercises��history��

- &emsp;&emsp;���ǿ��Զ����еĹ������Ͻ��б��ݡ�����������Ӳ�̻��˻��ߵ��Զ��ˣ�������վ����һ�ݱ��ݡ�

- &emsp;&emsp;���ǿ��Գ����ض��Լ��Ĺ��������ġ�Git֧�����Ƕ����е����ݴ�����֧��������գ��ϲ��޸ĵȣ������ǿ��Բ��ϵظĽ���Ʒ����Ӱ��ԭ�еİ汾��

Git���ļ���������ͼ

![](../images/git-015.PNG)

&emsp;&emsp;1. Checkout����һ��ʹ����Ҫ��Զ�̷�����fetch��checkout HEAD���������صĹ���Ŀ¼��֮�����Ǳ�����ڹ���Ŀ¼����������/ɾ��/�޸��ļ���Ȼ���ύ�����صĲֿ⡣

&emsp;&emsp;2. Add to Index����������ӵ��ļ�������Ҫ�����ӵ�������Add to Index�����棬�ļ����޸ĲŻ����Git�ĸ��ٷ�Χ��

&emsp;&emsp;3. Commit������������������ļ��� ����ֻ��Ҫ��Ҫ������ĵ�ʱ����һ�����ύ�����زֿ⡱��Commit���Ĳ�������ô���ļ��ĸ��ı��ڱ�������ʷ��Ѱ��

&emsp;&emsp;4. Push/Pull��ͬ�����زֿ⣨Local Repository����Զ�ֿ̲⣨Remote Repository���ļ�¼�������õĶ��ʺ�����Push���ǰѱ��زֿ�ļ�¼���͵��������ϣ���Pull���ǰѷ������ļ�¼�������صĲֿ⡣

***������΢����һ�£�����Git��һ��DVCS��Distributed Version Control System���ֲ�ʽ�汾����ϵͳ������ͬ�ڴ�ͳ��CVS/SVN�汾ϵͳ����������һ��������������������еİ汾��¼����ʵ����ÿһ���ֿⶼ�ɶ�����������˶���Ϊ�ֲ�ʽ��Distributed����Git Repos�ȿ�����һ���������Ĳֿ⣬Ҳ������һ�����ص��ļ��ֿ⣬���Դ����벻ͬ���ļ��������˵ĵ����ϣ������Ա������Ƶ�fork/clone������֧�������������ǵ����Σ�upstream����Դ����һ����֧��������ӵ����ͬupstream�Ĳֿ�֮�䣬�Ϳ��Թ���汾��Ϣ�Խ��а汾�ϲ�������***

##github�����

&emsp;&emsp;github��git��Ŀ�й���վ�������������һ��github�ʺţ�www.github.com

##github�ͻ���

&emsp;&emsp;Git:�ֲ�ʽ�汾���ƹ���

###windows��ʹ�ý���

####׼������

#####windows��git����

**1.tortoisegit**

&emsp;&emsp;tortoisegit��������tortoisesvn�Ĺ���

���ص�ַ��http://download.tortoisegit.org/tgit/1.8.14.0/

ִ��Ĭ�ϰ�װ�������ɣ��һ���ᷢ�ֶ��������ݼ����޷���ͼ��

**2.msysgit**

github�Ƿ���ˣ�Ҫ�����Լ�������ʹ��git���ǻ���Ҫһ��git�ͻ��ˣ�������ѡ��msysgit�����ֻ���ṩ��git�ĺ��Ĺ��ܣ������ǻ��������еġ�

���ص�ַ��http://msysgit.github.io/

ִ��Ĭ�ϰ�װ�������ɣ�dos��ִ��git�����Ƿ�װ�ɹ������ִ�в��ɹ�����Ҫ����һ�»�������path=C:\Program Files (x86)\Git\bin

Ȼ��ִ��git�������ͼ��ʾ��װ�ɹ�

![](../images/git-001.PNG)

**3.git for windows**

���ص�ַ��https://windows.github.com/

Ĭ�ϲ�����װ���ɣ���װ���˫���򿪳ɹ�����ʾ��װ�ɹ�


####����һ

ʹ��tortoisegit��msysgit����

**1.����SSH KEY**

&emsp;&emsp;GitHubѡ���Ĭ��ͨ�ŷ�ʽ��SSH������Ҫ����Git��������ssh key����Git Bash�����������������
ssh-keygen -t rsa -C "your_email@example.com"

&emsp;&emsp;֮�������ѡ���Ƿ�Դ��SSH Key���ļ��н��м��ܣ�һ�㶼����Ҫ�ġ�һ·�س�����OK�ˡ�

&emsp;&emsp;��c�̣���ǰ�û��ļ����£��и�.ssh�ļ��У�������ҵ� id_rsa.pub�ļ����ü��±��򿪣��������е�ȫ�����ݡ�
��½���GitHub�˻������ε��Account Settings > SSH Public Keys > Add another public key����id_rsa.pub�е����ݿ�����key�У�title��ѡ��
���ˣ������������Ѿ�����ˡ�

**2.Ȼ��git clone�����ع���**

![](../images/git-012.png)

**3.ִ��git commit -> master**

![](../images/git-012.png)

**4.���ύ�ɹ��Ĳ����ο���ͼ**

![](../images/git-013.png)

####������

ֻʹ��msysgit����

![](../images/git-010.png)

˵����1.git clone�����ع���

2.�л�������Ŀ¼

3.git add ������Ҫ�ύ���ļ�

git status�ǲ鿴�޸ĵ��ļ���add���Ϊ��ɫ��

4.git commit���ύ����

5.git push���ύ��github�����

����������Բο�git help

![](../images/git-011.png)

####������

ʹ��git for windows����

**1.����github����˹���**

˫����github���ߣ���Ҫ��¼github�˺ţ���¼��ҳ������

![](../images/git-002.PNG)

Ȼ��Ҫ����github�ϵĹ��̣���������ͼ

![](../images/git-003.png)

Ȼ����clone��Ȼ��ѡ��clone·��

![](../images/git-004.png)

���ع�������

![](../images/git-005.png)

������ɺ�

![](../images/git-006.png)

**2.�ϴ��޸�����**

������޸ĵĻ�������ͼ��ʾ

![](../images/git-007.png)

commit֮������ͼ��ʾ

![](../images/git-008.png)

Ȼ����syncͬ��������ʾ����ͼ����ʾ�ϴ�ok

![](../images/git-009.png)

####ע��

github����˹��̹������ڸ��ӹ��̹�ϵ��

Ʃ�����ǵ��������ǣ�https://github.com/NUST-Encryption-program/project-information

��ʹ�ô˹���ʱ����Ҫfork���̣���ֹ�����޸ĵĳ�ͻ

Ʃ��fork�Ĺ����ǣ�https://github.com/gaoyanshou/project-information

�������еĲ�����Ҫ��fork�Ĺ����н��У��������أ��ϴ�

######��Ҫ����

��ʱ����������Push���µ���������ʱ�򣬷��ַ������ϵİ汾�Ѿ��б��˸��¹��ˣ������µ������˵�Push��¼û�����ص����أ���ʱ��Ҫ�����Ȱѱ��˵ĸ������ص����أ���ȷ���Լ��ǻ������°��ύ�ĸ��ģ��ſ��԰ѱ��صļ�¼Push��ȥ����������޸ĵĲ��ָ��Լ��Ĳ���û���غϣ���Ӧ�ÿ����Զ���merge��













