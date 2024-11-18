
Tên hàm: getNRWProfileByKyNam
**Input**: options: any
options {
period: Kỳ
year: Năm
}

Phương thức query: Feature Layer (Sử dụng link)

query params: 
```js
queryParams.where = `level_ = 'dma'`;
queryParams.returnGeometry = false;

if (options.year && options.period) {
queryParams.where += ` AND year = ${options.year} AND period = ${options.period}`;
} else {
queryParams.orderByFields = ["year DESC", "period DESC"];
}
```

Query dựa trên kỳ và năm

**Output**: Object {`year, period, id, profileId`}

! Xử lý nếu chưa chọn kỳ và năm (*Period and Year*)
- Lấy năm đầu tiên trong data features trả về
- `Period` default là 4

```js
const getNRWProfileByKyNam = async (options: any = {}) => {
try {
const fLNRWProfile: FeatureLayer = createFeatureLayer(
layerNRWUrl.ANRWProfile)

if (!fLNRWProfile) {
return undefined
} 

const queryParams = fLNRWProfile.createQuery()
queryParams.where = `level_ = 'dma'`
queryParams.returnGeometry = false

if (options.year && options.period) {
queryParams.where += ` AND year = ${options.year} AND period = ${options.period}`
} else {
queryParams.orderByFields = ["year DESC", "period DESC"]
} 

const results = await fLNRWProfile.queryFeatures(queryParams)

if (!options.year && !options.period) {
const { year, period } = results?.features[0]?.attributes
setYearSelected(dayjs().year(year))
// setPeriodSelected(period);
setPeriodSelected(4) // tạm default là 4
setFirstLoad(true)
}
return results?.features?.map(f => f.attributes)
} catch (error) {}
}
```
