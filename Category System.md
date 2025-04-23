方面类别用于定义评论中所表达观点所涉及的方面类型。我们从针对笔记本电脑的 SemEval-2015 task 12中获得灵感，将其方面类别体系调整到智能手机领域。
该分类系统包含两种主要类型的标签：实体标签和属性标签。每个实体标签与属性标签的唯一组合会形成一个“方面类别”标签。
<br>
实体标签可以是整部手机（例如 Apple iPhone 15）、手机的有形部分（例如屏幕）或抽象部分（例如分辨率），也可以是制造公司（例如 Apple）以及其提供的服务（例如售前及售后客户支持）。
属性标签表示与每个实体标签相关的特定的质量或特征。
下表分别展示了 16 个预定义的实体标签与 8 个预定义的属性标签，以及它们的描述。
<br>
The category defines the type of aspect involved in the opinion expressed in the review. 
We adapt the aspect category system from SemEval-2015 Task 12 for laptops \cite{pontiki-etal-2015-semeval} to the smartphone domain.
The category system comprises two primary types of labels: \textbf{Entity Labels} and \textbf{Attribute Labels}. 
Each unique pair of an entity and an attribute label defines an **Aspect Category Label**.
<br>
An entity label can refer to the whole phone (e.g. Apple iPhone 15), its tangible components (e.g. screen) and abstract parts (e.g. resolution), 
the manufacturing company (e.g. Apple) or the services it provides (e.g. pre- and after-sales customer support). 
An attribute label denotes the specific qualities or characteristics associated with each entity label. 
Table~\ref{tab:entity_label} and table~\ref{tab:attribute_label} respectively show 16 predefined entity labels and 8 predefined attribute labels, along with their descriptions.
<br>
Entity Label(16) | Description
----| ----
PHONE | Phone as a whole.
DISPLAY | Display screen, external screen, internal screen, etc.
PROCESSOR | CPU.
MEMORY&STORAGE | Running memory and storage space.
CAMERA | Camera, front camera, rear camera, etc.
BATTERY&POWER | Battery and power supply (charger, charging cable).
COMMUNICATION | Internet connectivity (4G, 5G), Wi-Fi, Bluetooth, etc.
COOLING | Fans, cooling systems, radiators, etc.
AUDIO DEVICES | Sound, speakers, headphones, vibration motors, etc.
PHYSICAL INTERFACE | SIM card slot, physical buttons (power button, volume buttons), ports (Type-C port, Lightning port), and more.
ACCESSORY | Cell phone case, cell phone film, matching earphone, stylus and so on.
HARDWARE | Overall hardware configuration.
OS | Operating systems and their functions.
APP | Software applications, such as preinstalled apps (memos, settings, browser, etc.).
SERVICE | Pre- and post-sales customer support, customer service, repair services, product support, replacement policies and staff.
BRAND | Brands and Companies.

