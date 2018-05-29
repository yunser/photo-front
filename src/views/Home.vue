<template>
    <my-page title="证件照片排版在线生成器">
        <form id="sandphotoform" class="form-horizontal" action="http://tool2.yunser.com/sandphoto/sandphoto.php" method="POST" enctype="multipart/form-data">
            <div class="form-group">
                <label class="control-label col-xs-3">例子</label>
                <div class="col-xs-9 col-sm-3">
                    <img class="preview-img" src="/static/img/demo2.jpg" alt="">
                </div>
            </div>
            <div class="form-group">
                <label class="control-label col-xs-3" for="target_type">照片尺寸</label>
                <div class="col-xs-9 col-sm-3">
                    <select id="target_type" class="form-control" name="target_type">
                        <option value="0">1寸 (2.50cm * 3.50cm)</option>
                        <option value="1">大一寸 (3.30cm * 4.80cm)</option>
                        <option value="2">小一寸 (2.20cm * 3.20cm)</option>
                        <option value="3">彩色大一寸 (4.00cm * 5.50cm)</option>
                        <option value="4">彩色小一寸 (2.70cm * 3.80cm)</option>
                        <option value="5">黑白大一寸 (3.30cm * 4.80cm)</option>
                        <option value="6">黑白小一寸 (2.20cm * 3.20cm)</option>
                        <option value="7">2寸 (3.80cm * 5.10cm)</option>
                        <option value="8">大二寸 (3.50cm * 5.00cm)</option>
                        <option value="9">小二寸 (3.50cm * 4.50cm)</option>
                        <option value="10">身份证 (2.20cm * 3.20cm)</option>
                        <option value="11">第二代身份证 (2.60cm * 3.20cm)</option>
                        <option value="12">驾驶证 (2.20cm * 3.20cm)</option>
                        <option value="13">中国护照 (3.30cm * 4.80cm)</option>
                        <option value="14">赴美非移民签证 (5.10cm * 5.10cm)</option>
                        <option value="15">赴美移民签证 (3.50cm * 4.00cm)</option>
                        <option value="16">加拿大签证 (3.50cm * 4.50cm)</option>
                        <option value="17">英国签证 (3.50cm * 4.50cm)</option>
                        <option value="18">澳大利亚签证 (3.30cm * 4.80cm)</option>
                        <option value="19">日本签证 (4.50cm * 4.50cm)</option>
                        <option value="20">港澳通行证 (3.30cm * 4.80cm)</option>
                        <option value="21">香港特区护照 (4.00cm * 5.00cm)</option>
                        <option value="22">普通证件照 (3.30cm * 4.80cm)</option>
                        <option value="23">机动车行驶证 (6.00cm * 8.80cm)</option>
                        <option value="24">毕业生照 (3.30cm * 4.80cm)</option>
                        <option value="25">在美申请申根签证 (3.00cm * 4.00cm)</option>
                        <option value="32">阿根廷签证 (4.00cm * 4.00cm)</option>
                        <option value="33">意大利签证 (4.50cm * 3.50cm)</option>
                    </select>
                    <p class="help-clock">选择你要冲洗的证件照片的尺寸</p>
                </div>
            </div>
            <div class="form-group">
                <label class="control-label col-xs-3" for="container_type">总大小</label>
                <div class="col-xs-9 col-sm-3">
                    <select id="container_type" class="form-control" name="container_type">
                        <option value="26">5寸(3R) (12.70cm * 8.90cm)</option>
                        <option value="27">6寸(4R) (15.20cm * 10.20cm)</option>
                        <option value="28">7寸(5R) (17.80cm * 12.70cm)</option>
                        <option value="29">8寸(6R) (20.30cm * 15.20cm)</option>
                        <option value="30">10寸(8R) (25.40cm * 20.30cm)</option>
                        <option value="31">12寸 (25.40cm * 30.48cm)</option>
                    </select>
                    <p class="help-clock">选择用多大的照片冲洗（一般选择6寸的就好，这个价格最合适）</p>
                </div>
            </div>
            <div class="form-group">
                <label class="control-label col-xs-3" for="bgcolorid">背景颜色</label>
                <div class="col-xs-9 col-sm-3">
                    <input id="bgcolorid" type="radio" name="bgcolorid" value="blue" checked="checked"> 蓝色
                    <input id="bgcolorid" type="radio" name="bgcolorid" value="white"> 白色
                </div>
            </div>
            <div class="form-group">
                <label class="control-label col-xs-3">预览</label>
                <div class="col-xs-9 col-sm-3">
                    <img id="previewImg" alt="" src="preview.php?t=0&amp;c=27&amp;b=blue">
                </div>
            </div>
            <div class="form-group">
                <label class="control-label col-xs-3" for="filename">选择你的证件照片</label>
                <div class="col-xs-9 col-sm-3">
                    <input id="filename" class="form-control " type="file" name="filename">
                </div>
            </div>
            <div class="form-group">
                <div class="col-xs-9 col-sm-3 col-xs-offset-3">
                    <input class="btn btn-success" type="submit" value="下载">
                    <p class="help-clock">如果你的照片比较大， 上传会花一些时间， 别着急， 请耐心等待。</p>
                </div>

            </div>
        </form>
    </my-page>
</template>

<script>
    /* eslint-disable */
    export default {
        data () {
            return {
            }
        },
        mounted() {
            function updatePreview() {
                let $target_type = $("#target_type option:selected").val();
                let $container_type = $("#container_type option:selected").val();
                let $bgcolorid= $("#sandphotoform input:radio:checked").val();
                if ($target_type && $container_type && $bgcolorid) {
                    $("#previewImg").attr("src", "http://tool2.yunser.com/sandphoto/preview.php?t=" + $target_type + "&c=" + $container_type + "&b=" + $bgcolorid);
                }
            }

            function checkForm() {
                if ($("#filename").val() == "")
                {
                    alert("请选择照片后再试");
                    return false;
                }
                if (!$("#filename").val().match(/jpg|jpeg|png|tiff/i))
                {
                    alert("只支持jpeg, jpg, png, tiff文件");
                    return false;
                }


                return true;
            }

            $("#target_type").change(updatePreview);
            $("#container_type").change(updatePreview);
            $("#sandphotoform input:radio").click(updatePreview);
            $("#sandphotoform").submit(checkForm);
            updatePreview();

        }
    }
</script>

<style scoped>
.preview-img {
	width:  120px;
	height: 200px;
}
</style>
