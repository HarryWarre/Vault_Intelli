Tên function: getDataGttnCompany
Input: {`Period: Kỳ, Year: Năm`}
Output: 

Sử dụng phương thức: Axios

```js
const res = await axios.post(
	apiUrls.getNRWTheoLuuLuongCongTy_ByYear,
		{ year: yearData },
		{
		headers: {
			"Content-Type": "application/json",
			"x-api-key": apiUrls.apiKey,
		},
	}
)
```

Xử lý kết quả query về:

- Hàm con: divideTwoColumnsAggregationFn
Xử lý: Chia 2 cột giá trị
