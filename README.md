# �Զ�������ƽ̨
## ��ܽ���
* ����python3
* ����app UI�Զ�����ʹ��appium��������ios,�Ͱ�׿��

### 2015-10-10 ������־
* testBaseOpreate ͨ�ò���������򵥵㣬ִ�в�������ȡxml(yaml�����ļ�)
* testCase ���������ļ�����������
* testData ���Եĳ������ݣ���ö������
* testMode ����ʵ����
* testSetting���Կ�ܵĳ�������
* testRunner �������� runner.py���
* testReport ���չʾ
	* ������pyh�ֶ�ƴ��htmlҳ��ķ�ʽ
	* ���Խ�������� Junit ��ʽ�� xml �ļ���Ȼ����������������
	

## 2015-11-10 ������־
* ����yaml�����ò��԰���������xml
* �������Զ�����־����
* �������󻯣������еĵط�ֻҪ�޸�testDriver.webChatHome.py ���ɣ������ط������޸�

## 2016-1-19 ������־
* �淶markdown�﷨

## 2016-3-25
* �����������Ĺ�������ֻ��D:\appium\testcase\module(��Ŀģ��)�����Լ���������
* testCaseĿ¼��д��Ӧ�ļ���ִ�в�������
```yaml�����ļ�
 - element_info: com.xfb.user:id/home_fragment_arrow_left_img
   operate_type: click
   findElemtType: id
 - element_info: com.xfb.user:id/citydeals_item_title
   operate_type: null
   findElemtType: id
```
 * ��һ�������ǲ���
 * �ڶ��������Ǽ���

* ���չʾ�Ż�
 * ������ͼ
 * ����������־��ִ����־�ֿ���ʾ
``` ������Ϣ
 2016-03-25 18:03:14,098 - root - INFO - ----  test_check_home   START     ----
``` 
``` ִ����־
 test_click_home: OK
``` 
* ���������Ż���ʹ��setUpClass tearDownClass ����setup,teardown��ÿ��ִ��������case�Ż�ر�app


## 2016-4-28 ������־
* ������unittest��������ÿ��ֻҪ  suite.addTest(TestInterfaceCase.parametrize(testShiBase)) �࣬�Ϳ���ִ����������������case����ڱ����runner4.py

* �������չʾ,���õ���pyhƴ�ӵķ�ʽ������html����

![report.png](img/report.png "report.png")


## 2016-7-24������־

* �Ż�������

```
class getOperateElement():
    def __init__(self, driver=""):
        self.cts = driver
    def findElement(self, elemt_by, element_info):
        '''
        ����Ԫ��
        :param elemt_by:   ��������,id,xpath��
        :param element_info: ����Ԫ�ز�������xpath��ֵ��id��ֵ
        :return:
        '''
        try:
            WebDriverWait(self.cts, 10).until(lambda x: elements_by(elemt_by, self.cts, element_info))
            return True
        except selenium.common.exceptions.TimeoutException:
            return False
        except selenium.common.exceptions.NoSuchElementException:
            print("�Ҳ�������")
            return False
    def operate_element(self, operate, elemen_by, element_info, *arg):
        '''
        ���еĲ������
        :param operate: ������Ӧcommon�е�click,tap��
        :param elemen_by: ��Ӧcommon�е�id,xpath,name��
        :param element_info: ��ϸ��Ԫ�أ���xpath�ĸ�ʽ����id,name������
        :param arg: ��չ�ֶδ�list
        :return:
        '''
        elements = {
            common.CLICK: lambda: operate_click(elemen_by, self.cts, element_info),
            common.TAP: lambda: operate_tap(elemen_by, self.cts, elemen_by, arg)
        }
        return elements[operate]()

# ����¼�
def operate_click(elemen_by,cts,element_info):
    elements_by(elemen_by, cts, element_info).click()

# ���x�������ƶ�x��λ��y�������ƶ�y��λ
def operate_tap(elemen_by,cts,element_info, xy=[]):
    elements_by(elemen_by, cts, element_info).tap(x=xy[0], y=xy[1])

# ��װ���õ�find��ǩ
def elements_by(types, cts, element_info):
    elements = {
        common.ID : lambda :cts.find_element_by_id(element_info),
        common.XPATH: lambda :cts.find_element_by_xpath(element_info),
        common.NAME: lambda :cts.find_element_by_name(element_info)
    }
    return elements[types]()

```

# 2016-7-29 ������־
* [��װappium-server����](https://github.com/284772894/appiumn_auto/blob/master/testRunner/testServer.py)
* [schematics����model��Ĺ���](https://github.com/284772894/appiumn_auto/blob/master/testMode/BaseAppDevices.py)����ȫȡ����ͳ��get set,���һ�����֤�ֶε������Ƿ���ȷ

# 2016-8-6 ������־
* ʹ�������ķ�ʽ����appium
* �Ż�������д�࣬�Ժ�ֻҪ��������yaml�ļ�������case.py��������

```
# ����������������
execCase(r'D:\appium\testcase\home\home_more_adv.yaml', test_id="2004", test_intr="��ҳ���", test_case="test_home_more_adv",isLast="1")

```

# 2016-8-26
* ���²��Ա��棬��excelչʾ
* �ʼ����Ͳ��Ա���

![testReport.png](img/testReport.png "testReport.png")

![testReportDetail.png](img/testReportDetail.png "testReportDetail.png")

![testEmail.png](img/testEmail.png "testMail.png")

# 2016-9-5
* ����ܹ��ع�����ϵͳ����Ϊ��model,dal,bll,common,testCase(��Ҫ��д����),runner����ڣ�
* ���¼�¼�ڴ棬cpu,ƽ��������ֵ���

# 2016-9-6
* �޸������ڴ����
* �Ż��������

# 2016-8-7
* �ع�DAL����DAL�����⣬�ŵ���common������ȥ��


# 2016-9-21
* ������¼������־�����������ˣ����ڱ������һ�β�����־����Ϊ������˺󣬻�ֹͣ���У����Ը������һ��������˵���־�ҵ������
	* �����Ż����˺󣬻���������������к���case,�Ƚ��鷳����ʱ��û�кõ�˼·
* ����ִ��caseʧ�ܺ󣬽�ͼ������
* ���������ͼ����������־
* �����Ż���¼��־�ͱ�����������
