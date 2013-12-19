---
layout: post
title: "Ha noi se xay ham vuot song hong"
date: 2013-12-18 09:52:18 +0700
comments: true
categories: [javascript,nodejs,express]
---
TT - Tin từ Sở Giao thông vận tải Hà Nội ngày 17-12 cho biết Bộ Xây dựng vừa có báo cáo thẩm định đồ án quy hoạch phát triển giao thông thủ đô Hà Nội đến năm 2030, tầm nhìn đến năm 2050. <!--more-->

Theo đồ án này, Hà Nội sẽ xây dựng tổng thể 15 cầu, trong đó có tám cầu vượt sông Đuống, ba cầu vượt sông Đà và các cầu vượt sông Đáy.

Cùng với đó, Hà Nội sẽ có năm cảng hàng không và sân bay, bao gồm: cảng hàng không quốc tế Nội Bài, các sân bay Gia Lâm, Bạch Mai, Miếu Môn, Hòa Lạc.

{% codeblock lang:objc %}
[rectangle setX: 10 y: 10 width: 20 height: 20];
{% endcodeblock %}

Đáng chú ý, một hầm ngầm xuyên qua sông Hồng sẽ được xây dựng nhằm đáp ứng nhu cầu lưu thông cho người dân thủ đô.

{% codeblock lang:javascript server.js %}

	/*!
	 * nodejs-express-mongoose-demo
	 * Copyright(c) 2013 Madhusudhan Srinivasa <madhums8@gmail.com>
	 * MIT Licensed
	 */

	/**
	 * Module dependencies.
	 */

	var express = require('express')
	  , fs = require('fs')
	  , passport = require('passport')

	/**
	 * Main application entry file.
	 * Please note that the order of loading is important.
	 */

	// Load configurations
	// if test env, load example file
	var env = process.env.NODE_ENV || 'development'
	  , config = require('./config/config')[env]
	  , mongoose = require('mongoose')

	// Bootstrap db connection
	mongoose.connect(config.db)

	// Bootstrap models
	var models_path = __dirname + '/app/models'
	fs.readdirSync(models_path).forEach(function (file) {
	  if (~file.indexOf('.js')) require(models_path + '/' + file)
	})

	// bootstrap passport config
	require('./config/passport')(passport, config)

	var app = express()
	// express settings
	require('./config/express')(app, config, passport)

	// Bootstrap routes
	require('./config/routes')(app, passport)

	// Start the app by listening on <port>
	var port = process.env.PORT || 3000
	app.listen(port)
	console.log('Express app started on port '+port)

	// expose app
	exports = module.exports = app

{% endcodeblock %}

Trao đổi với Tuổi Trẻ liên quan tới việc xây dựng hầm ngầm này, ông Nguyễn Quốc Hùng, giám đốc Sở Giao thông vận tải Hà Nội, cho hay đây là chủ trương nằm trong quy hoạch chung thủ đô được Thủ tướng phê duyệt trước đó, do vậy đương nhiên nằm trong quy hoạch giao thông thủ đô.

“Dự kiến hầm vượt sẽ xuất phát từ phía cuối đường Trần Hưng Đạo (khu vực ngoài đê) vượt sông Hồng qua Long Biên” - ông Hùng nói.
