---
order: 2
zh-CN:
	title: Loading
	product: 商品
	longName: 听说这样设置一个超长超长的商品名会不换行
	alignRight: 听说这样设置访问量可以靠右对齐
	bigStock: 这是一个大库存
en-US:
	title: Loading
	product: Product
	longName: a very very looooooooonnnnng name
	alignRight: right alignment
	bigStock: big size
---

```jsx

import { Grid, Switch } from 'zent';

const columns = [
	{
		title: '{i18n.longName}',
		name: 'name',
		width: 100,
		nowrap: true
	}, {
		title: '{i18n.alignRight}',
		name: 'uv',
		textAlign: 'right',
		width: 300
	}, {
		title: '{i18n.bigStock}',
		name: 'stock',
		className: 'big-size'
	}
];

const datasets = [];

for (let i = 0; i < 3; i++) {
	datasets.push({
		name: `{i18n.product} ${i}`,
		uv: 20,
		stock: 5
	})
}

class Loading extends React.Component {
	state={
		loading: true
	}
	render() {
		return (
			<div>
				<Switch
					onChange={value => this.setState({ loading: value })}
					checked={this.state.loading}
					size="small"
					className="switch"
				/>
				<Grid
					columns={columns}
					datasets={datasets}
					loading={this.state.loading}
				/>
			</div>
		);
	}
};

ReactDOM.render(
		<Loading />
	, mountNode
);

```
