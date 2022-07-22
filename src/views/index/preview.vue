
<script>

function findGetParameter(parameterName) {
    var result = null,
        tmp = [];
    location.hash.split('?')[1]
        .substr(0)
        .split("&")
        .forEach(function (item) {
          tmp = item.split("=");
          if (tmp[0] === parameterName) result = decodeURIComponent(tmp[1]);
        });
    return result;
}

let params = findGetParameter('postData')
const code = JSON.parse(params).data
let main = eval(`(${code.js})`)
main.template = `<div>${code.html}</div>`
export default {
  name: 'preview-main',
  data(){
    return {
      preRender: {}
    }
  },
  components: {
    preview: main
  },
  created(){
  
  },
  mounted(){},
  template: `<div><preview /></div>`
}
</script>
<style lang='less' scoped>
</style>
