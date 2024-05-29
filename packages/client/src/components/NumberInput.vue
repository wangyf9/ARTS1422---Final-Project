<template>
	<div class="input-container">
	  <input
		type="number"
		class="number-input"
		placeholder="Press ID"
		v-model.number="number"
		@keydown.enter="emitNumber"
		@blur="emitNumber"
	  />
	</div>
  </template>
  
<script>
import bus from '../common/utils/bus';
  
export default {
	data() {
		return {
		number: 0,
		};
	},	
	props: {
		selectedId1: {
			required: true
		},
		selectedId2: {
			required: true
		},
	},
	methods: {
		emitNumber() {
		// 确保数字在0到1010之间
		if (this.number < 0) {
			this.number = 0;
		} else if (this.number > 1010) {
			this.number = 1010;
		}
		// 通过总线发送数字
			// this.$emit('update:selectedId', this.number,0);
			console.log("emit success =======",this.number);
		},
	},
	};
</script>

<style scoped>
.number-input {
padding: 5px; /* 输入框内边距 */
border: 1px solid #ccc; /* 边框样式 */
border-radius: 5px; /* 边框圆角 */
box-shadow: 0 2px 5px rgba(0, 0, 0, 0.2); /* 输入框阴影 */
font-size: 14px; /* 字体大小 */
}
</style>
  