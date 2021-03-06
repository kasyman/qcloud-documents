## 1. 接口描述
 
本接口（DescribeFlowLogs）用于查询流日志列表。
接口请求域名：<font style="color:red">vpc.api.qcloud.com</font> 


## 2. 输入参数
以下请求参数列表仅列出了接口请求参数，正式调用时需要加上公共请求参数，见 <a href="/doc/api/372/4153" title="公共请求参数">公共请求参数</a> 页面。其中，此接口的 Action 字段为 DescribeFlowLogs。

| 参数名称 | 必选  | 类型 | 描述 |
|---------|---------|---------|---------|
| vpcId | 否 | String | 流日志所属的私有网络 ID 值，可使用 vpcId 或 unVpcId，建议使用 unVpcId，例如：vpc-kd7d06of，可通过 <a href="http://cloud.tencent.com/doc/api/245/%E6%9F%A5%E8%AF%A2%E7%A7%81%E6%9C%89%E7%BD%91%E7%BB%9C%E5%88%97%E8%A1%A8" title="DescribeVpcEx">DescribeVpcEx</a> 接口查询。 | 
| flowLogId | 否 | String | 系统分配的流日志 ID，支持模糊查询，例如：fl-3lzrkspo。|
| flowLogName | 否 | String | 流日志名称，支持模糊查询。 |
| resourceType | 否 | String | 流日志所属资源类型，VPC，SUBNET，NETWORKINTERFACE。 |
| resourceId | 否 | String | 资源唯一 ID，例如 vpc-puz6fg，subnet-5o8ycyt，eni-08dhim。 |
| trafficType | 否 | String | 流日志采集类型，ACCEPT，REJECT，ALL。 |
| cloudLogId | 否 | String | 流日志存储 ID, 暂时只支持日志服务 ID，例如 d44e4cf0-c3e2-48d9-bb64-c5f0337ef2b0。 |
| cloudLogState | 否 | String | 流日志存储 ID 状态。 |
| limit | 否 | Int | 每页行数，默认为 10。 |
| orderField | 否 | String | 按某个字段排序，支持字段：flowLogName，createTime，默认按 createTime。 |
| orderDirection | 否 | String | 升序（asc）还是降序（desc），默认：desc。 |
| offset | 否 | Int | 初始行的偏移量，默认为 0。|

## 3. 输出参数

| 参数名称 | 类型 | 描述|
|---------|---------|---------|
| code| Int | 错误码，0：成功，其他值：失败。 |
| message |  String | 错误信息。 |
| totalCount |  Int | 流日志总数量。 |
| data | Array  | 返回的数组。 |
| data.n.vpcId | String | 系统分配的 vpcId，例如：vpc_dfadfad。|
| data.n.flowLogId | String | 系统分配的流日志 ID，支持模糊查询，例如：fl-3lzrkspo。|
| data.n.flowLogName | String | 流日志名称，支持模糊查询。 |
| data.n.resourceType | String | 流日志所属资源类型，VPC，SUBNET，NETWORKINTERFACE。 |
| data.n.resourceId | String | 资源唯一 ID，例如vpc-puz6fg，subnet-5o8ycyt，eni-08dhim。 |
| data.n.trafficType | String | 流日志采集类型，ACCEPT，REJECT， ALL。 |
| data.n.cloudLogId | String | 流日志存储 ID，暂时只支持日志服务 ID，例如 d44e4cf0-c3e2-48d9-bb64-c5f0337ef2b0。 |
| data.n.cloudLogState | String | 流日志存储 ID 状态。 |


## 4. 错误码表
以下错误码表仅列出了该接口的业务逻辑错误码，更多公共错误码详见 <a href="https://cloud.tencent.com/doc/api/245/4924" title="VPC错误码">VPC错误码</a>。
 
| 错误码 | 描述 |
|---------|---------|
| InvalidVpc.NotFound | 无效的 VPC。VPC 资源不存在，请再次核实您输入的资源信息是否正确，可通过 <a href="http://cloud.tencent.com/doc/api/245/%E6%9F%A5%E8%AF%A2%E7%A7%81%E6%9C%89%E7%BD%91%E7%BB%9C%E5%88%97%E8%A1%A8" title="DescribeVpcEx">DescribeVpcEx</a> 接口查询 VPC。 |

## 5. 示例
 
输入
<pre>
  https://vpc.api.qcloud.com/v2/index.php?Action=DescribeFlowLogs
  &<<a href="https://cloud.tencent.com/doc/api/229/6976">公共请求参数</a>>
  &vpcId=vpc-idg1prjj
</pre>

输出

```
{
    "code": 0,
    "message": "",
    "codeDesc": "Success",
    "data": {
        "totalNum": 1,
        "data": [
            {
                "vpcId": "vpc-iqg1prjj",
                "flowLogId": "fl-1pq1g9x1",
                "flowLogName": "test_rtt",
                "resourceType": "NETWORKINTERFACE",
                "resourceId": "eni-a35i4igb",
                "trafficType": "ACCEPT",
                "cloudLogId": "4fb6a027-dc83-4dae-94fc-3d995025a239",
                "cloudLogState": "SUCCESS",
                "flowLogDescription": "",
                "createdTime": "2017-12-22 11:25:35"
            }
        ]
    }
}
```
