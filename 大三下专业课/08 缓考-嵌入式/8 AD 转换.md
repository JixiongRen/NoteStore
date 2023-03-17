#### 8.1 A/D 转换的四个步骤

* **采样 -> 保持 -> 量化 -> 编码**
	* 采样/保持：由采样保持电路（S/H）完成；
	* 量化/编码：由 ADC 电路完成（ADC：AD 转换器）
* **采样**：将一个时间上**连续**变化的模拟量转化为时间上**断续**变化的模拟量（连续 -> 离散）
* **保持**：将采样得到的模拟量值保持下来，使之等于采样控制脉冲存在的最后瞬间的采样值。
* **量化**：是用基本的量化电平的个数来表示采样到模拟电压值。即把时间上离散而数值上连续的模拟量以一定的准确度变换为时间上、数值上都离散的具有标准量化级的等效数字值。（量化电平的大小取决于 A/D 变换器的字长）
* **编码**：是把已经量化的模拟数值 (它一定是量化电平的整数倍) 用二进制码、BCD 码或其它码来表示。

#### 8.2 香农采样定理

为了不失真地恢复模拟信号，采样频率应该大于等于模拟信号频谱中最高频率的 2 倍，即：$f_s ≥ 2f_{max}$ 

#### 8.3 A/D 转换控制程序的编制步骤

1. 设置 A/D 转换的时钟频率——取决于 ADCCON 寄存器的 PRSCVL 的值，计算式 $\mathrm{PRSCVL=\frac{PCLK}{freq} -1}$ 
2. 启动 A/D 转换：`rADCCON = 0x01;`
3. 检查转换是否结束：`while(rADCCON & 0x8000);`
4. 启动读允许功能：`rADCCON = 0x02;`
5. 读 A/D 转换数据：`uint i = rADCDAT0 & 0x3FF;`

#### 8.4 实验五 A/D 转换实验

>旋转电位器的位置，通过 S3C2440X 的 AD 转换器模拟通道 0，将电阻上的电压值转换成数字量，并将数字量数据换成十进制浮点数（小数点后 2 位），同时，十进制浮点数通过 UART0 发送至 PC 机的串口调试助手（波特率 115200、1 位停止位、无校验位、无硬件流控制）中显示。
>> 提示：数字量数据 usConData 换成十进制浮点数，并输出：
>> `usEndData=usConData*3.3000/0x3FF;`
>> `uart_printf (" %0.2f ", usEndData); `

```C
#include "def.h"
#include "option.h"
#include "2440addr.h"    
#include "2440lib.h"
#include "2440slib.h"  
#define UINT32T unsigned int  

/*******函数声明区*******/
void uart0_init(void); // 串口初始化函数
void uart_sendbyte(float data); // 发送字符函数
void AD_Init(unsigned char ch); // AD初始化函数
int Get_AD(unsigned char ch); // AD转换函数

/*******主函数*******/
void main(int argc, char **argv)
{
    uart0_init(); //初始化串口
    while(1)
    {                      
        int num; 
        float dat;
        AD_Init(0);    //初始化AD转换器  
        num = Get_AD(0);            //取AD转换后的值
        dat = num * 3.3000/0x3FF;   //转为要求的数据格式
        Uart_Printf("%.2f\n",dat);  //输出在串口
        uart_sendbyte(dat);         //发送至电脑
    }            
}

/*******功能函数定义*******/

/**
@brief 串口初始化，参考串口实验
*/
void uart0_init(void)   
{
    rGPHCON=(rGPHCON&~(0xfff<<4))|(0xaaa<<4);  
    rGPHUP=rGPHUP|(0x7<<2);                          
    rUFCON0=0x0;                                      
    rUMCON0=0x0;                                      
    rULCON0=(rULCON0&~0xff)|((0x0<<6)|(0x0<<3)|(0x0<<2)|(0x3));
    rUCON0=(rUCON0&~0x3ff)|((0x0<<10)|(0x0<<6)|(0x1<<2)|(0x1));
    // 波特率115200
    rUBRDIV0=(int)(50000000/(16*115200)-1);     
}

/**
@brief 串口发送数据，参考串口实验，但要注意数据类型为float
@param data 待发送的数据
*/
void uart_sendbyte(float data) 
{
    while(!(rUTRSTAT0&0x02));            
    rUTXH0=data;                                      
}

/**
@brief AD转换初始化
@param ch 选择的通道号
*/
void AD_Init(unsigned char ch)            
{
  rADCDLY=100;//P296 ADC起始延时寄存器
  rADCTSC=0;
  rADCCON=(1<<14)|(49<<6)|(ch<<3)|(0<<2)|(0<<1)|(0);
}

/**
@brief 取AD转换的值，这部分可直接参考PPT
@param ch 选择的通道号
*/
int Get_AD(unsigned char ch)   //取A/D转换的值
{
  int i;
  int val=0;
  if(ch>7) return 0;
  for(i=0;i<16;i++) //为转换准确，转换16次
  {
    rADCCON|=0x1;   //启动A/D转换
    rADCCON= rADCCON & 0xFFC7|(ch<<3); //选择A/D通道
    while( rADCCON & 0x1);        //等待A/D转换开始
    while(!(rADCCON & 0x8000));   //等待A/D转换结束
    val=val+(rADCDAT0 & 0x03ff);  //取值
    Delay(10);
  }
  return(val>>4);  // 右移4位相当于除以16，返回每次转换均值
}
```
