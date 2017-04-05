# Info

`info`包含一些关于你原型的常用信息，比如项目名或作者名。他将作为分享流的一部分，并且在你将作品分享到线上或者Facebook和Twitter上时显示。
>The info variable is used to store general information about your prototype, such as project title or author. This information is used as part of the sharing flow, and the information will appear when you share a project online or via Facebook and Twitter.

你可以通过这种方式给你的用户写一些说明，添加你的个人标识或者你Twitter和个人网站的链接。
>Adding this information to your project is a great way to leave instructions for your user, add identity to your project and link to your Twitter profile or website.

你可以按如下方式自定义你的分享信息。
>Here's how you can customize your Sharing Info:

    Framer.Info =
        author: "Koen Bok"
        twitter: "@koenbok"
        title: "My Pretty Project"
        description: "Just some sample."

如果你想在预览时看见自己的分享信息，可以这么写：
>If you would like to see a sharing preview in Framer:

	Framer.Extras.ShareInfo.enable()

`info`中可以包含的信息（全部都是可选）：
>The supported attributes are (all optional):

* **author** — 作者名称 (比如：小明)。
* **twitter** — 作者的twitter唯一标示（要写成类似@jsone格式）。
* **title** — 项目名称(默认为文件名)。
* **description** — 简短的项目描述，支持添加链接。
* **date** — 发布日期(默认为上传日期)。
* **image.facebook** — Open graph image url for Facebook card（宝宝也不知道是啥）.
* **image.twitter** — Twitter card image url（宝宝也不知道是啥）.