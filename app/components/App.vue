<template>
    <Page>
        <ActionBar title="Welcome to NativeScript-Vue!" android:flat="true"/>
        <TabView android:tabBackgroundColor="#53ba82"
                 android:tabTextColor="#c4ffdf"
                 android:selectedTabTextColor="#ffffff"
                 androidSelectedTabHighlightColor="#ffffff">
            <TabViewItem title="Tab 1">
                <GridLayout columns="*" rows="*">
                    <Label class="message" :text="msg" col="0" row="0"/>
                </GridLayout>
            </TabViewItem>
            <TabViewItem title="Tab 2">
                <GridLayout columns="*" rows="*,*">
					<Button text="ボタン1" class="button" col="0" row="0,0" backgroundColor="#1c6b48" @tap="displayAlert()"/>
					<Button text="ボタン2" class="button" col="0" row="1,0" backgroundColor="#1c6b48" @tap="$goto('sample2')"/>
                
				</GridLayout>
            </TabViewItem>
        </TabView>
    </Page>
</template>

<script >
	import axios from "axios";
  export default {
	methods: {
		onButtonTap(){
			console.log("hogehoge");
		},
		displayAlert(){
			axios({
				method: "GET", "url": "https://pokeapi.co/api/v2/pokemon/?limit=151" })
				.then(function(result) {
					result.data.results.forEach(function (value) {
						console.log(value.name);
					});
					alert("hogehoge");
				}, function(error) {
					console.error(error);
			});
		}
	},
    data() {
      return {
        msg: 'Hello World!'
      }
    }
  }
</script>

<style scoped>
    ActionBar {
        background-color: #53ba82;
        color: #ffffff;
    }

    .message {
        vertical-align: center;
        text-align: center;
        font-size: 20;
        color: #333333;
    }
</style>
