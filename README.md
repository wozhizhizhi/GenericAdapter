#通用的listviewAdapter
##怎么使用
1.将代码下载,里面有2个类,将这两个类拷贝到你自己的项目
2.继承FuBaseAdapter

```
public class HomeFuAdapter extends FuBaseAdapter<HomeBean>
{
    // 构造方法
    public HomeFuAdapter(AbsListView listView, List<HomeBean> mDatas)
    {
        super(listView, mDatas, R.layout.home_item);
    }

    // 实现convert方法
    @Override
    public void convert(FuHodlerView helper, HomeBean item, boolean isScrolling)
    {
        Context context = helper.getConvertView().getContext();
        if(isScrolling)
        {
            ImageView imageView = helper.getView(R.id.home_item_icon);
            ImageLoadUtils.loadImage(context , item.getImageUrl().getUrl() ,imageView);
        }
        else
        {
            helper.setImageByUrl(context , R.id.home_item_icon , item.getImageUrl().getUrl());
        }

        helper.setText(R.id.home_item_text , item.getTitle());
        helper.setText(R.id.home_item_price , item.getPrice());
    }
```
