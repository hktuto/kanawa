<template>
    <div>
        <div align="center">
	<table border="1" width="700" height="55" id="table41" style="border-collapse:collapse" bordercolorlight="#000000" bordercolordark="#000000">
		<tr>
			<td style="border-style: none; border-width: medium" width="760" height="55">
			    <img border="0" src="/images/banner.jpg" width="700" height="55">
            </td>
		</tr>
	</table>
</div>
<div align="center">
	<table border="1" width="704" id="table42" style="border-collapse: collapse; " bordercolorlight="#000000" bordercolordark="#000000" height="548">
		<tr>
			<td style="border-style: none; border-width: medium" width="153" align="center" valign="top" bordercolorlight="#C0C0C0" bordercolordark="#C0C0C0">
			<div align="left">
			<div  v-for="item in menu " :key="item.url" align="left">
                <!-- menu  -->
            <table border="1" width="150" id="table65" style="border-collapse:collapse; border-bottom-width:0px" bordercolorlight="#C0C0C0" bordercolordark="#C0C0C0" height="25" bgcolor="#D0BDAF">
				<tr>
					<td style="border-left-style:solid; border-left-width:1px; border-right-style:solid; border-right-width:1px; border-top-style:solid; border-top-width:1px; border-bottom-style:none; border-bottom-width:medium" bordercolorlight="#C0C0C0" bordercolordark="#C0C0C0">
					  <b>&#8231;<a :href="item.url">{{item.label}}</a></b></td>
				</tr>
			</table>
			
			</div>
			
			<div align="left" style="height: 391px; background-color: #D0BDAF;">
            </div>
			</div>
			</td>
			<td style="border-style: none; border-width: medium" align="center" valign="top">
                <div class="contentContainer">
			        <slot />
                </div>
			</td>
		</tr>
	</table></div>
<p align="center"><font color="#333300"><span style="font-size: 7pt"><span lang="en">&copy;</span>Copyright.
The Kanawa Company Limited 2002-2006. All rights reserved</span></font></p>

</div>
</template>

<script lang="ts" setup>
    const menu = [
        {
            label:"主頁",
            url:"/",
        },
        {
            label:"企業簡介",
            url:"/about",
        },
        {
            label:'企業設備',
            url:"/equipment"
        },
        {
            label:'產品展示',
            url:"/product"
        },
        {
            label:'企業責任',
            url:"/responsibility"
        },
        {
            label:'聯絡我們',
            url:"/contact"
        },
    ]
</script>

<style scoped>

    form {margin:-2 0 0; border-style: none}
    
    .searchButtonBlack { 
    font-family: Arial;
    font-size: 11px;
    font-weight: 700;
    text-decoration: none;
    color: #FFFFFF;
    background-color: #000000;
    border: 0px;
    width: 80px;
    height: 20px;
    cursor: pointer; 
    } 
    #searchBoxButton { 
    width: 88px;
    height: 23px;
    vertical-align: top;
    margin: 1px 0px 0px 0px; 
    }
.contentContainer{
    width:551px;
    padding-inline: 24px;
    height:547px;
    overflow: auto;
    text-align: left;
}
</style>