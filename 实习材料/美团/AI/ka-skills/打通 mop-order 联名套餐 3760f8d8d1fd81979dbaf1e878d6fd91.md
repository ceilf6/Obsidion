# 打通 mop-order 联名套餐

Source: [KM 2759161502](https://km.sankuai.com/collabpage/2759161502)

[image.png](https://km.sankuai.com/api/file/cdn/2759161502/234190236594?contentType=1&isNewContent=false)

由于联名套餐返回的数据格式和普通商品的不一致

## 响应对比

### 正常响应

```
// 代码块
{
  "data": {
    "pageId": "12413",
    "pageProtocolId": "0350",
    "pageProtocolVersion": "0001",
    "bizRespStatus": {
      "isError": false,
      "errorToast": true,
      "extra": null
    },
    "struct": [
      {
        "n": "MeishiCommonDuoParams"
      },
      {
        "n": "TopBottomSlide",
        "s": {
          "renderModuleNodes": [
            {
              "n": "MeishiGroupBuyTab"
            },
            {
              "n": "MopContainer"
            },
            {
              "n": "MopDataContainer"
            },
            {
              "n": "AfterPay"
            },
            {
              "n": "BottomFill"
            }
          ],
          "renderTop": [
            {
              "n": "DzBgLineargradient"
            }
          ],
          "renderBackground": [
            {
              "n": "MaxLeezCard",
              "s": {
                "children": [
                  {
                    "n": "MaxLeezCard1"
                  },
                  {
                    "n": "DzBgLineargradient2"
                  }
                ]
              }
            }
          ],
          "renderTopChildren": [
            {
              "n": "TopTag"
            }
          ]
        }
      },
      {
        "n": "Dialog"
      },
      {
        "n": "MeishiKaMopDuoSubmitRemindModal"
      },
      {
        "n": "MeishiKaMopCheckShopModal"
      },
      {
        "n": "SubmitRisk"
      },
      {
        "n": "MeishiFoodGroupSubmitLogic"
      },
      {
        "n": "FoodSubmitStatic"
      }
    ],
    "logics": [
      {
        "n": "MeishiCommonDuoLifecycle1"
      },
      {
        "n": "MeishiCommonEventNav1"
      },
      {
        "n": "MeishiUtilAutoReporterInstance1"
      },
      {
        "n": "MeishiCommonEventLx1"
      }
    ],
    "nodeDataMap": {
      "MeishiCommonDuoParams": {
        "i": "757",
        "p": {
          "lxCommonParams": {
            "channelName": "meishi",
            "pageInfoKey": "group-order-submit",
            "commonParams": {
              "is_mvp": "0",
              "deal_id": "1340587375",
              "poi_id": "1851844943",
              "tab_name": 0,
              "is_distribute": 0,
              "source": "-999",
              "scene_type": "1",
              "deal_sale_count": -999,
              "deal_count": "-999",
              "distribute_deal_count": -999,
              "bundle_product_source": 0,
              "page_version": "2",
              "page_module": "0",
              "has_text": 0,
              "submit_deal_info": "-999",
              "is_person_order_same_phone_number": 0,
              "is_person_login_same_phone_number": 0,
              "is_null": 1
            },
            "cid": "c_meishi_rao5v99i"
          },
          "themeColor": {
            "mainColorValue": "#FF4B10"
          }
        },
        "pc": {
          "magicMemberPreview": {
            "r": true
          }
        }
      },
      "TopBottomSlide": {
        "i": "136",
        "p": {
          "keyboardAvoidBehavior": "padding",
          "keyboardVerticalOffset": 180,
          "moduleNodeConfigs": [
            {
              "n": "TetuanIpTips",
              "p": 1
            },
            {
              "n": "MeishiGroupBuyTab",
              "p": 1
            },
            {
              "n": "KaMopSingleTitle",
              "p": 1
            },
            {
              "n": "CartGroupDealListBg",
              "p": 2
            },
            {
              "n": "CartGroupDealList",
              "p": 2
            },
            {
              "n": "MopDataContainer",
              "p": 2
            },
            {
              "n": "MopContainer",
              "p": 1
            },
            {
              "n": "MeishiTopLinear",
              "p": 2
            },
            {
              "n": "Notice",
              "p": 2
            },
            {
              "n": "Product",
              "p": 2
            },
            {
              "n": "ProductTips",
              "p": 2
            },
            {
              "n": "GroupSubmitGiftTips",
              "p": 2
            },
            {
              "n": "TotalPrice",
              "p": 2
            },
            {
              "n": "Desk",
              "p": 2
            },
            {
              "n": "Card1",
              "p": 2
            },
            {
              "n": "Total",
              "p": 2
            },
            {
              "n": "MagicmemberPreview",
              "p": 2
            },
            {
              "n": "VipCard",
              "p": 2
            },
            {
              "n": "TieSale",
              "p": 2
            },
            {
              "n": "TieInSaleV3",
              "p": 2
            },
            {
              "n": "PayType",
              "p": 2
            },
            {
              "n": "PayFront",
              "p": 2
            },
            {
              "n": "InvitePay",
              "p": 2
            },
            {
              "n": "AfterPay",
              "p": 2
            },
            {
              "n": "Authorization",
              "p": 2
            },
            {
              "n": "BottomFill",
              "p": 2
            },
            {
              "n": "BottomBar",
              "p": 3
            }
          ],
          "sliderMaxHeight": "95%",
          "statusBarStyle": "dark-content",
          "hideKeyboardOnScroll": false,
          "safeAreaBottom": "none",
          "showSlideModal": true,
          "maskClosable": true,
          "statusBarTranslucent": true,
          "slideCloseKey": "CLOSE_POP_SLIDER_MODAL",
          "hiddenLifecycleComponent": true,
          "keyboardShouldPersistTaps": "handled",
          "slideClosePage": true,
          "disableDownClosePage": false,
          "sliderHeight": "85.0%",
          "scrollStyle": {
            "paddingLeft": 8,
            "paddingRight": 8
          },
          "loadingkey": "group-order-submit",
          "bounces": true,
          "hasMetric": true,
          "hiddenSkeleton": true
        },
        "s": {
          "slideModalStyle": {
            "borderTopRightRadius": 20,
            "borderTopLeftRadius": 20
          },
          "contentStyle": {
            "backgroundColor": "transparent"
          },
          "bottomStyle": {
            "backgroundColor": "#f7f7f7",
            "position": "relative",
            "bottom": 0,
            "zIndex": 2
          },
          "bottomSafeAreaStyle": {
            "backgroundColor": "#fff"
          },
          "topStyle": {
            "backgroundColor": "#f7f7f7",
            "position": "relative"
          }
        }
      },
      "MeishiGroupBuyTab": {
        "i": "397",
        "p": {
          "buyScene": "1",
          "pageScene": 5,
          "pureBgColor": true,
          "tabInfoList": [
            {
              "pageScene": 5,
              "tabTitle": "秒提·到店取",
              "tabTag": "3",
              "tabStyle": 0
            },
            {
              "pageScene": 1,
              "tabTitle": "买团购",
              "tabTag": "3",
              "tabStyle": 0
            }
          ],
          "multiTabScene": 1,
          "queryTabType": "5",
          "lx": {
            "channelName": "meishi",
            "pageInfoKey": "group-order-submit",
            "commonParams": {
              "is_mvp": "0",
              "deal_id": "1340587375",
              "poi_id": "1851844943",
              "tab_name": 0,
              "is_distribute": 0,
              "source": "-999",
              "scene_type": "1",
              "deal_sale_count": -999,
              "deal_count": "-999",
              "distribute_deal_count": -999,
              "bundle_product_source": 0,
              "page_version": "2",
              "page_module": "0",
              "has_text": 0,
              "submit_deal_info": "-999",
              "is_person_order_same_phone_number": 0,
              "is_person_login_same_phone_number": 0,
              "is_null": 1
            },
            "cid": "c_meishi_rao5v99i"
          }
        },
        "s": {
          "wrapStyle": {
            "marginRight": 0,
            "backgroundColor": "transparent",
            "paddingLeft": 0,
            "marginLeft": 0,
            "paddingRight": 0,
            "zIndex": 1
          }
        },
        "pc": {
          "pageScene": {
            "r": true
          },
          "multiTabScene": {
            "r": true
          },
          "cartTempProductList": {
            "r": true
          }
        },
        "e": {
          "e": {
            "defaultOnTabClick": [
              {
                "n": "MeishiGroupSubmitMrnWapper",
                "e": "onTableClick",
                "t": [
                  {
                    "t": "tabItem",
                    "f": ""
                  }
                ]
              }
            ],
            "onTabClick": [
              {
                "n": "MopContainer",
                "e": "onMiaoTiUpdate",
                "t": [
                  {
                    "t": "tabType",
                    "f": ""
                  },
                  {
                    "t": "payload.tabSelect",
                    "f": ""
                  }
                ]
              }
            ]
          }
        }
      },
      "MopContainer": {
        "i": "413",
        "p": {
          "transferData": {
            "quantity": "1"
          },
          "pageQuery": {
            "mrn_transparent": "true",
            "mrn_biz": "meishi",
            "mrn_entry": "c-group-order-submit",
            "tabType": "5",
            "nibBizConsistency": "gmV2peeKZ5C2xJqoC9o14IlfIQJKqkO42Jf4ABsGz-8KD454ZUT648SFJb5Xmlo-W7hOiYrFcmjrzrm7sfnYubZN2_5zY5kTi2UrHKeoMvVrT5nT3t9GrhskJchFCoLwliEF1s34nZteNndoTq4p6jumFIat5E7x3OHWWfcsj4dLvGLpZX3OuprG5Z4aEmDaoMyq9sp2llHJnwzKWZ-JHeeaBOwWgg9awIgxp2w6d0M",
            "trafficSourceActivityId": "",
            "sec_source": "rhhj_dd",
            "isOnlyShowShopCart": "false",
            "mrn_component": "GroupOrderSubmit",
            "isDealJudge": "",
            "_referer": "food-poi",
            "flexibleJSON": "",
            "mrn_hideNextNavBar": "true",
            "hideLoading": "true",
            "groupBuyMopScene": "1",
            "hasKNBParams": "1",
            "venueId": "",
            "mlive_ext": "",
            "buyPoiIdEncrypt": "qB4r17707da606bc98ea64a037925971660ee8e63d7690a06106e1ce2a76ee607d88922f49ead8b8b2b7712a292610e43d2bac167cdcda7719f50f20vxu5",
            "source": "",
            "mrn_adjustParentFrame": "true",
            "productType": "",
            "dealId": "1340587375",
            "lng": "121.52897062950872",
            "halfScreenSubmitHeight": "0.85",
            "payPrice": "14.9",
            "showPrice": "14.9",
            "shelfFusion": "true",
            "lat": "31.273660438522672",
            "dd_source": "",
            "mrn_hideloading": "true",
            "govPromotion": "",
            "isTransparent": "true",
            "buyPoiId": "1851844943",
            "mrn_min_version": "2.115.0",
            "campaignId": ""
          },
          "commonParam": {
            "location": {
              "lat": "31.273660438522672",
              "lng": "121.52897062950872",
              "accuracy": "7.230641488784651"
            },
            "isSubmit": "",
            "storage": {},
            "isUpdate": "",
            "fingerprint": {
              "fingerprint": ""
            },
            "isCheck": "",
            "isPreview": "true",
            "cityInfo": {
              "cityId": "10",
              "locCityId": "10"
            },
            "systemInfo": {
              "IS_HOTEL": "",
              "mpAppVersion": "",
              "userAgent": "",
              "version": "12.56.200",
              "isWeb": "",
              "mpPluginAppId": "",
              "IS_TICKET": "",
              "isDebug": "",
              "IS_DP": "",
              "envInWeb": {},
              "platform": "ios",
              "systemVersion": "26.3.1",
              "mpAppId": "",
              "IS_MT": "true",
              "isMRN": "true",
              "isWeChatMiniProgram": "",
              "device": ""
            },
            "userInfo": {
              "uuidV2": "00000000000007A0030108A0C430C88DF8E7BA59BF348A177457840783633080",
              "userId": "3842765890",
              "mtuuid": "00000000000007A0030108A0C430C88DF8E7BA59BF348A177457840783633080",
              "unionId": "8b854f09f2814f2cb120f473ac3930eea176350111025506278",
              "uuid": "00000000000007A0030108A0C430C88DF8E7BA59BF348A177457840783633080",
              "token": "AgFsIpe7YXQee_IBR4ln-oXXq_F6jtq2AOMT_6oEuvwbZm3IQkWpq9RK7ZiTZb-EXRonInIFDWyzYAAAAAAENAAA2w_Qkp6xP7nbBz0_CIKZwutJA8YJUz3UHNqjoIPrlkhqnK4I_I3ifwXnnfUT-7KV",
              "dpid": ""
            }
          },
          "tabInfoList": [
            {
              "pageScene": 5,
              "tabTitle": "秒提·到店取",
              "tabTag": "3",
              "tabStyle": 0
            },
            {
              "pageScene": 1,
              "tabTitle": "买团购",
              "tabTag": "3",
              "tabStyle": 0
            }
          ],
          "tabHeight": 44,
          "effectiveScreenPer": "85.0%",
          "onlineOrderPropsVo": {
            "mopShopInfoVO": {
              "shopId": "1851844943",
              "shopIcon": "<https://p0.meituan.net/40.40/travelcube/7b5cf1381d1f3c7e1d0896a84dcc56c627952.jpg>",
              "shopName": "瑞幸咖啡（互联宝地二期店）",
              "shopAddress": "杨浦区黄兴路221号互联宝地二期负1层B1-68",
              "chooseShopUrl": "imeituan://www.meituan.com/mrn?mrn_biz=meishi&mrn_entry=ka-mop-poi-select&mrn_component=kaMopPoiSelect&dishSource=10&shopId=1851844943&dealId=1340587375&brandId=288&jumpToShopSelectPageOnLoad=true&pageSource=instant-order-page",
              "distance": 228,
              "distanceDesc": "228m",
              "brandId": "288",
              "topTipList": [
                {
                  "content": "附近有多家门店，请确认是否在本店取餐",
                  "type": 0
                }
              ],
              "bottomTipList": [],
              "topTipRichTextList": [
                {
                  "content": "<span style='color: #888888;'>距您228m，杨浦区黄兴路221号互联宝地二期负1层B1-68</span>",
                  "type": 0
                },
                {
                  "content": "<span style='color: #888888;'>附近有<span style='color: #FF4B10;'>多家门店</span>，请确认取餐门店</span>",
                  "type": 0
                }
              ],
              "tipList": []
            },
            "mopBrandInfoVO": {
              "brandId": "288",
              "mopBrandType": 20
            },
            "mopDealMappingInfoVO": {
              "mopDealMappingProductInfoVO": {
                "dealId": 1340587375,
                "dealIdStr": "1340587375",
                "dealTag": 1,
                "dealName": "【耶加系列】3选1",
                "mappingId": "66081150",
                "dealMappingType": 20,
                "dealMappingChooseType": 3,
                "mopDealProductGroupList": [
                  {
                    "groupName": "品质SOE系列 3选1",
                    "groupId": 84047472,
                    "maxChoiceNum": 1,
                    "minChoiceNum": 1,
                    "canRepeatChoose": true,
                    "mopProductList": [
                      {
                        "spuName": "耶加雪菲美式",
                        "spuId": "840897641",
                        "isAvailable": true,
                        "spuPicAddr": "<https://img.meituan.net/shopdirectconnectpic/3f907c6abc2c55da04e5c1f7ba785ddc.jpg>",
                        "defaultSkuId": "2878743098",
                        "mopSkuList": [
                          {
                            "skuId": "2878743098",
                            "spuId": "840897641",
                            "skuName": "小黑杯",
                            "isAvailable": true,
                            "isSupplementSku": false,
                            "currentPrice": "2900",
                            "originalPrice": "2900",
                            "addPrice": "0",
                            "stockCount": -1,
                            "mopSkuSaleAttrList": [
                              {
                                "groupCode": "64",
                                "attributeId": "416241906"
                              }
                            ],
                            "mopCustomRuleList": [
                              {
                                "premiumGroupCode": "17",
                                "defaultSelect": true,
                                "mustSelect": true,
                                "maxChoice": 1,
                                "minChoice": 1,
                                "defaultSelectNum": 1,
                                "unitPerStep": 1,
                                "exchange": false,
                                "hide": false,
                                "fold": false,
                                "rank": 1,
                                "ruleType": 10,
                                "multiChoice": false,
                                "groupMultiChoice": false
                              },
                              {
                                "premiumGroupCode": "14",
                                "defaultSelect": true,
                                "mustSelect": true,
                                "maxChoice": 1,
                                "minChoice": 1,
                                "defaultSelectNum": 1,
                                "unitPerStep": 1,
                                "exchange": false,
                                "hide": false,
                                "fold": false,
                                "rank": 2,
                                "ruleType": 10,
                                "multiChoice": false,
                                "groupMultiChoice": false
                              },
                              {
                                "premiumId": "2559254875",
                                "premiumGroupCode": "17",
                                "defaultSelect": false,
                                "mustSelect": false,
                                "maxChoice": 1,
                                "minChoice": 0,
                                "maxFreeNum": 0,
                                "defaultSelectNum": 1,
                                "unitPerStep": 1,
                                "exchange": false,
                                "hide": false,
                                "rank": 1,
                                "ruleType": 20,
                                "multiChoice": false,
                                "groupMultiChoice": false,
                                "price": "0",
                                "premiumName": "冰"
                              },
                              {
                                "premiumId": "2559371838",
                                "premiumGroupCode": "14",
                                "defaultSelect": false,
                                "mustSelect": false,
                                "maxChoice": 1,
                                "minChoice": 0,
                                "maxFreeNum": 0,
                                "defaultSelectNum": 1,
                                "unitPerStep": 1,
                                "exchange": false,
                                "hide": false,
                                "rank": 1,
                                "ruleType": 20,
                                "multiChoice": false,
                                "groupMultiChoice": false,
                                "price": "0",
                                "premiumName": "标准甜"
                              },
                              {
                                "premiumId": "2559322629",
                                "premiumGroupCode": "17",
                                "defaultSelect": true,
                                "mustSelect": false,
                                "maxChoice": 1,
                                "minChoice": 0,
                                "maxFreeNum": 0,
                                "defaultSelectNum": 1,
                                "unitPerStep": 1,
                                "exchange": false,
                                "hide": false,
                                "rank": 2,
                                "ruleType": 20,
                                "multiChoice": false,
                                "groupMultiChoice": false,
                                "price": "0",
                                "premiumName": "热"
                              },
                              {
                                "premiumId": "2559393711",
                                "premiumGroupCode": "14",
                                "defaultSelect": false,
                                "mustSelect": false,
                                "maxChoice": 1,
                                "minChoice": 0,
                                "maxFreeNum": 0,
                                "defaultSelectNum": 1,
                                "unitPerStep": 1,
                                "exchange": false,
                                "hide": false,
                                "rank": 2,
                                "ruleType": 20,
                                "multiChoice": false,
                                "groupMultiChoice": false,
                                "price": "0",
                                "premiumName": "少甜"
                              },
                              {
                                "premiumId": "2559354186",
                                "premiumGroupCode": "14",
                                "defaultSelect": false,
                                "mustSelect": false,
                                "maxChoice": 1,
                                "minChoice": 0,
                                "maxFreeNum": 0,
                                "defaultSelectNum": 1,
                                "unitPerStep": 1,
                                "exchange": false,
                                "hide": false,
                                "rank": 3,
                                "ruleType": 20,
                                "multiChoice": false,
                                "groupMultiChoice": false,
                                "price": "0",
                                "premiumName": "少少甜"
                              },
                              {
                                "premiumId": "2559380169",
                                "premiumGroupCode": "14",
                                "defaultSelect": false,
                                "mustSelect": false,
                                "maxChoice": 1,
                                "minChoice": 0,
                                "maxFreeNum": 0,
                                "defaultSelectNum": 1,
                                "unitPerStep": 1,
                                "exchange": false,
                                "hide": false,
                                "rank": 4,
                                "ruleType": 20,
                                "multiChoice": false,
                                "groupMultiChoice": false,
                                "price": "0",
                                "premiumName": "微甜"
                              },
                              {
                                "premiumId": "2559418501",
                                "premiumGroupCode": "14",
                                "defaultSelect": true,
                                "mustSelect": false,
                                "maxChoice": 1,
                                "minChoice": 0,
                                "maxFreeNum": 0,
                                "defaultSelectNum": 1,
                                "unitPerStep": 1,
                                "exchange": false,
                                "hide": false,
                                "rank": 5,
                                "ruleType": 20,
                                "multiChoice": false,
                                "groupMultiChoice": false,
                                "price": "0",
                                "premiumName": "不另外加糖"
                              }
                            ]
                          }
                        ],
                        "mopProductAttrGroups": [
                          {
                            "groupName": "杯型",
                            "groupCode": "64",
                            "maxChoiceNum": 1,
                            "minChoiceNum": 1,
                            "isSellAttributeGroup": true,
                            "rank": 1,
                            "mopProductAttrItems": [
                              {
                                "attrId": "416241906",
                                "attrValue": "小黑杯",
                                "rank": 1,
                                "attrAddPrice": "0"
                              }
                            ]
                          },
                          {
                            "groupName": "温度",
                            "groupCode": "17",
                            "isSellAttributeGroup": false,
                            "multiChoice": false,
                            "chooseMultiPremium": false,
                            "rank": 1,
                            "mopProductAttrItems": [
                              {
                                "attrId": "2559254875",
                                "attrValue": "冰",
                                "rank": 1,
                                "attrAddPrice": "0"
                              },
                              {
                                "attrId": "2559322629",
                                "attrValue": "热",
                                "rank": 2,
                                "attrAddPrice": "0"
                              }
                            ]
                          },
                          {
                            "groupName": "糖",
                            "groupCode": "14",
                            "isSellAttributeGroup": false,
                            "multiChoice": false,
                            "chooseMultiPremium": false,
                            "rank": 2,
                            "mopProductAttrItems": [
                              {
                                "attrId": "2559371838",
                                "attrValue": "标准甜",
                                "rank": 1,
                                "attrAddPrice": "0"
                              },
                              {
                                "attrId": "2559393711",
                                "attrValue": "少甜",
                                "rank": 2,
                                "attrAddPrice": "0"
                              },
                              {
                                "attrId": "2559354186",
                                "attrValue": "少少甜",
                                "rank": 3,
                                "attrAddPrice": "0"
                              },
                              {
                                "attrId": "2559380169",
                                "attrValue": "微甜",
                                "rank": 4,
                                "attrAddPrice": "0"
                              },
                              {
                                "attrId": "2559418501",
                                "attrValue": "不另外加糖",
                                "rank": 5,
                                "attrAddPrice": "0"
                              }
                            ]
                          }
                        ],
                        "extendInfoMap": {},
                        "needQi": false
                      },
                      {
                        "spuName": "耶加雪菲拿铁",
                        "spuId": "840838517",
                        "isAvailable": true,
                        "spuPicAddr": "<https://img.meituan.net/shopdirectconnectpic/1dc2160099934ae0f02ac5b9050e502e.jpg>",
                        "defaultSkuId": "2878699915",
                        "mopSkuList": [
                          {
                            "skuId": "2878699915",
                            "spuId": "840838517",
                            "skuName": "小黑杯",
                            "isAvailable": true,
                            "isSupplementSku": false,
                            "currentPrice": "3200",
                            "originalPrice": "3200",
                            "addPrice": "0",
                            "stockCount": -1,
                            "mopSkuSaleAttrList": [
                              {
                                "groupCode": "64",
                                "attributeId": "416245679"
                              }
                            ],
                            "mopCustomRuleList": [
                              {
                                "premiumGroupCode": "17",
                                "defaultSelect": true,
                                "mustSelect": true,
                                "maxChoice": 1,
                                "minChoice": 1,
                                "defaultSelectNum": 1,
                                "unitPerStep": 1,
                                "exchange": false,
                                "hide": false,
                                "fold": false,
                                "rank": 1,
                                "ruleType": 10,
                                "multiChoice": false,
                                "groupMultiChoice": false
                              },
                              {
                                "premiumGroupCode": "14",
                                "defaultSelect": true,
                                "mustSelect": true,
                                "maxChoice": 1,
                                "minChoice": 1,
                                "defaultSelectNum": 1,
                                "unitPerStep": 1,
                                "exchange": false,
                                "hide": false,
                                "fold": false,
                                "rank": 2,
                                "ruleType": 10,
                                "multiChoice": false,
                                "groupMultiChoice": false
                              },
                              {
                                "premiumGroupCode": "102",
                                "defaultSelect": true,
                                "mustSelect": true,
                                "maxChoice": 1,
                                "minChoice": 1,
                                "defaultSelectNum": 1,
                                "unitPerStep": 1,
                                "exchange": false,
                                "hide": false,
                                "fold": false,
                                "rank": 3,
                                "ruleType": 10,
                                "multiChoice": false,
                                "groupMultiChoice": false
                              },
                              {
                                "premiumId": "2559417450",
                                "premiumGroupCode": "17",
                                "defaultSelect": false,
                                "mustSelect": false,
                                "maxChoice": 1,
                                "minChoice": 0,
                                "maxFreeNum": 0,
                                "defaultSelectNum": 1,
                                "unitPerStep": 1,
                                "exchange": false,
                                "hide": false,
                                "rank": 1,
                                "ruleType": 20,
                                "multiChoice": false,
                                "groupMultiChoice": false,
                                "price": "0",
                                "premiumName": "冰"
                              },
                              {
                                "premiumId": "2559477542",
                                "premiumGroupCode": "14",
                                "defaultSelect": false,
                                "mustSelect": false,
                                "maxChoice": 1,
                                "minChoice": 0,
                                "maxFreeNum": 0,
                                "defaultSelectNum": 1,
                                "unitPerStep": 1,
                                "exchange": false,
                                "hide": false,
                                "rank": 1,
                                "ruleType": 20,
                                "multiChoice": false,
                                "groupMultiChoice": false,
                                "price": "0",
                                "premiumName": "标准甜"
                              },
                              {
                                "premiumId": "2559424294",
                                "premiumGroupCode": "102",
                                "defaultSelect": true,
                                "mustSelect": false,
                                "maxChoice": 1,
                                "minChoice": 0,
                                "maxFreeNum": 0,
                                "defaultSelectNum": 1,
                                "unitPerStep": 1,
                                "exchange": false,
                                "hide": false,
                                "rank": 1,
                                "ruleType": 20,
                                "multiChoice": false,
                                "groupMultiChoice": false,
                                "price": "0",
                                "premiumName": "牛奶"
                              },
                              {
                                "premiumId": "2559523243",
                                "premiumGroupCode": "17",
                                "defaultSelect": true,
                                "mustSelect": false,
                                "maxChoice": 1,
                                "minChoice": 0,
                                "maxFreeNum": 0,
                                "defaultSelectNum": 1,
                                "unitPerStep": 1,
                                "exchange": false,
                                "hide": false,
                                "rank": 2,
                                "ruleType": 20,
                                "multiChoice": false,
                                "groupMultiChoice": false,
                                "price": "0",
                                "premiumName": "热"
                              },
                              {
                                "premiumId": "2559475737",
                                "premiumGroupCode": "14",
                                "defaultSelect": false,
                                "mustSelect": false,
                                "maxChoice": 1,
                                "minChoice": 0,
                                "maxFreeNum": 0,
                                "defaultSelectNum": 1,
                                "unitPerStep": 1,
                                "exchange": false,
                                "hide": false,
                                "rank": 2,
                                "ruleType": 20,
                                "multiChoice": false,
                                "groupMultiChoice": false,
                                "price": "0",
                                "premiumName": "少甜"
                              },
                              {
                                "premiumId": "2559411529",
                                "premiumGroupCode": "14",
                                "defaultSelect": false,
                                "mustSelect": false,
                                "maxChoice": 1,
                                "minChoice": 0,
                                "maxFreeNum": 0,
                                "defaultSelectNum": 1,
                                "unitPerStep": 1,
                                "exchange": false,
                                "hide": false,
                                "rank": 3,
                                "ruleType": 20,
                                "multiChoice": false,
                                "groupMultiChoice": false,
                                "price": "0",
                                "premiumName": "少少甜"
                              },
                              {
                                "premiumId": "2559398627",
                                "premiumGroupCode": "14",
                                "defaultSelect": false,
                                "mustSelect": false,
                                "maxChoice": 1,
                                "minChoice": 0,
                                "maxFreeNum": 0,
                                "defaultSelectNum": 1,
                                "unitPerStep": 1,
                                "exchange": false,
                                "hide": false,
                                "rank": 4,
                                "ruleType": 20,
                                "multiChoice": false,
                                "groupMultiChoice": false,
                                "price": "0",
                                "premiumName": "微甜"
                              },
                              {
                                "premiumId": "2559452808",
                                "premiumGroupCode": "14",
                                "defaultSelect": true,
                                "mustSelect": false,
                                "maxChoice": 1,
                                "minChoice": 0,
                                "maxFreeNum": 0,
                                "defaultSelectNum": 1,
                                "unitPerStep": 1,
                                "exchange": false,
                                "hide": false,
                                "rank": 5,
                                "ruleType": 20,
                                "multiChoice": false,
                                "groupMultiChoice": false,
                                "price": "0",
                                "premiumName": "不另外加糖"
                              }
                            ]
                          }
                        ],
                        "mopProductAttrGroups": [
                          {
                            "groupName": "杯型",
                            "groupCode": "64",
                            "maxChoiceNum": 1,
                            "minChoiceNum": 1,
                            "isSellAttributeGroup": true,
                            "rank": 1,
                            "mopProductAttrItems": [
                              {
                                "attrId": "416245679",
                                "attrValue": "小黑杯",
                                "rank": 1,
                                "attrAddPrice": "0"
                              }
                            ]
                          },
                          {
                            "groupName": "温度",
                            "groupCode": "17",
                            "isSellAttributeGroup": false,
                            "multiChoice": false,
                            "chooseMultiPremium": false,
                            "rank": 1,
                            "mopProductAttrItems": [
                              {
                                "attrId": "2559417450",
                                "attrValue": "冰",
                                "rank": 1,
                                "attrAddPrice": "0"
                              },
                              {
                                "attrId": "2559523243",
                                "attrValue": "热",
                                "rank": 2,
                                "attrAddPrice": "0"
                              }
                            ]
                          },
                          {
                            "groupName": "糖",
                            "groupCode": "14",
                            "isSellAttributeGroup": false,
                            "multiChoice": false,
                            "chooseMultiPremium": false,
                            "rank": 2,
                            "mopProductAttrItems": [
                              {
                                "attrId": "2559477542",
                                "attrValue": "标准甜",
                                "rank": 1,
                                "attrAddPrice": "0"
                              },
                              {
                                "attrId": "2559475737",
                                "attrValue": "少甜",
                                "rank": 2,
                                "attrAddPrice": "0"
                              },
                              {
                                "attrId": "2559411529",
                                "attrValue": "少少甜",
                                "rank": 3,
                                "attrAddPrice": "0"
                              },
                              {
                                "attrId": "2559398627",
                                "attrValue": "微甜",
                                "rank": 4,
                                "attrAddPrice": "0"
                              },
                              {
                                "attrId": "2559452808",
                                "attrValue": "不另外加糖",
                                "rank": 5,
                                "attrAddPrice": "0"
                              }
                            ]
                          },
                          {
                            "groupName": "奶基",
                            "groupCode": "102",
                            "isSellAttributeGroup": false,
                            "multiChoice": false,
                            "chooseMultiPremium": false,
                            "rank": 3,
                            "mopProductAttrItems": [
                              {
                                "attrId": "2559424294",
                                "attrValue": "牛奶",
                                "rank": 1,
                                "attrAddPrice": "0"
                              }
                            ]
                          }
                        ],
                        "extendInfoMap": {},
                        "needQi": false
                      },
                      {
                        "spuName": "耶加雪菲·澳瑞白",
                        "spuId": "840928420",
                        "isAvailable": true,
                        "spuPicAddr": "<https://img.meituan.net/shopdirectconnectpic/e28b7c7c5ba91185a42a904542f69678.jpg>",
                        "defaultSkuId": "2878738635",
                        "mopSkuList": [
                          {
                            "skuId": "2878738635",
                            "spuId": "840928420",
                            "skuName": "小黑杯",
                            "isAvailable": true,
                            "isSupplementSku": false,
                            "currentPrice": "3500",
                            "originalPrice": "3500",
                            "addPrice": "0",
                            "stockCount": -1,
                            "mopSkuSaleAttrList": [
                              {
                                "groupCode": "64",
                                "attributeId": "416270475"
                              }
                            ],
                            "mopCustomRuleList": [
                              {
                                "premiumGroupCode": "17",
                                "defaultSelect": true,
                                "mustSelect": true,
                                "maxChoice": 1,
                                "minChoice": 1,
                                "defaultSelectNum": 1,
                                "unitPerStep": 1,
                                "exchange": false,
                                "hide": false,
                                "fold": false,
                                "rank": 1,
                                "ruleType": 10,
                                "multiChoice": false,
                                "groupMultiChoice": false
                              },
                              {
                                "premiumGroupCode": "14",
                                "defaultSelect": true,
                                "mustSelect": true,
                                "maxChoice": 1,
                                "minChoice": 1,
                                "defaultSelectNum": 1,
                                "unitPerStep": 1,
                                "exchange": false,
                                "hide": false,
                                "fold": false,
                                "rank": 2,
                                "ruleType": 10,
                                "multiChoice": false,
                                "groupMultiChoice": false
                              },
                              {
                                "premiumId": "2559464094",
                                "premiumGroupCode": "17",
                                "defaultSelect": false,
                                "mustSelect": false,
                                "maxChoice": 1,
                                "minChoice": 0,
                                "maxFreeNum": 0,
                                "defaultSelectNum": 1,
                                "unitPerStep": 1,
                                "exchange": false,
                                "hide": false,
                                "rank": 1,
                                "ruleType": 20,
                                "multiChoice": false,
                                "groupMultiChoice": false,
                                "price": "0",
                                "premiumName": "冰"
                              },
                              {
                                "premiumId": "2559496038",
                                "premiumGroupCode": "14",
                                "defaultSelect": false,
                                "mustSelect": false,
                                "maxChoice": 1,
                                "minChoice": 0,
                                "maxFreeNum": 0,
                                "defaultSelectNum": 1,
                                "unitPerStep": 1,
                                "exchange": false,
                                "hide": false,
                                "rank": 1,
                                "ruleType": 20,
                                "multiChoice": false,
                                "groupMultiChoice": false,
                                "price": "0",
                                "premiumName": "标准甜"
                              },
                              {
                                "premiumId": "2559409759",
                                "premiumGroupCode": "17",
                                "defaultSelect": true,
                                "mustSelect": false,
                                "maxChoice": 1,
                                "minChoice": 0,
                                "maxFreeNum": 0,
                                "defaultSelectNum": 1,
                                "unitPerStep": 1,
                                "exchange": false,
                                "hide": false,
                                "rank": 2,
                                "ruleType": 20,
                                "multiChoice": false,
                                "groupMultiChoice": false,
                                "price": "0",
                                "premiumName": "热"
                              },
                              {
                                "premiumId": "2559554039",
                                "premiumGroupCode": "14",
                                "defaultSelect": false,
                                "mustSelect": false,
                                "maxChoice": 1,
                                "minChoice": 0,
                                "maxFreeNum": 0,
                                "defaultSelectNum": 1,
                                "unitPerStep": 1,
                                "exchange": false,
                                "hide": false,
                                "rank": 2,
                                "ruleType": 20,
                                "multiChoice": false,
                                "groupMultiChoice": false,
                                "price": "0",
                                "premiumName": "少甜"
                              },
                              {
                                "premiumId": "2559354772",
                                "premiumGroupCode": "14",
                                "defaultSelect": false,
                                "mustSelect": false,
                                "maxChoice": 1,
                                "minChoice": 0,
                                "maxFreeNum": 0,
                                "defaultSelectNum": 1,
                                "unitPerStep": 1,
                                "exchange": false,
                                "hide": false,
                                "rank": 3,
                                "ruleType": 20,
                                "multiChoice": false,
                                "groupMultiChoice": false,
                                "price": "0",
                                "premiumName": "少少甜"
                              },
                              {
                                "premiumId": "2559431388",
                                "premiumGroupCode": "14",
                                "defaultSelect": false,
                                "mustSelect": false,
                                "maxChoice": 1,
                                "minChoice": 0,
                                "maxFreeNum": 0,
                                "defaultSelectNum": 1,
                                "unitPerStep": 1,
                                "exchange": false,
                                "hide": false,
                                "rank": 4,
                                "ruleType": 20,
                                "multiChoice": false,
                                "groupMultiChoice": false,
                                "price": "0",
                                "premiumName": "微甜"
                              },
                              {
                                "premiumId": "2559455338",
                                "premiumGroupCode": "14",
                                "defaultSelect": true,
                                "mustSelect": false,
                                "maxChoice": 1,
                                "minChoice": 0,
                                "maxFreeNum": 0,
                                "defaultSelectNum": 1,
                                "unitPerStep": 1,
                                "exchange": false,
                                "hide": false,
                                "rank": 5,
                                "ruleType": 20,
                                "multiChoice": false,
                                "groupMultiChoice": false,
                                "price": "0",
                                "premiumName": "不另外加糖"
                              }
                            ]
                          }
                        ],
                        "mopProductAttrGroups": [
                          {
                            "groupName": "杯型",
                            "groupCode": "64",
                            "maxChoiceNum": 1,
                            "minChoiceNum": 1,
                            "isSellAttributeGroup": true,
                            "rank": 1,
                            "mopProductAttrItems": [
                              {
                                "attrId": "416270475",
                                "attrValue": "小黑杯",
                                "rank": 1,
                                "attrAddPrice": "0"
                              }
                            ]
                          },
                          {
                            "groupName": "温度",
                            "groupCode": "17",
                            "isSellAttributeGroup": false,
                            "multiChoice": false,
                            "chooseMultiPremium": false,
                            "rank": 1,
                            "mopProductAttrItems": [
                              {
                                "attrId": "2559464094",
                                "attrValue": "冰",
                                "rank": 1,
                                "attrAddPrice": "0"
                              },
                              {
                                "attrId": "2559409759",
                                "attrValue": "热",
                                "rank": 2,
                                "attrAddPrice": "0"
                              }
                            ]
                          },
                          {
                            "groupName": "糖",
                            "groupCode": "14",
                            "isSellAttributeGroup": false,
                            "multiChoice": false,
                            "chooseMultiPremium": false,
                            "rank": 2,
                            "mopProductAttrItems": [
                              {
                                "attrId": "2559496038",
                                "attrValue": "标准甜",
                                "rank": 1,
                                "attrAddPrice": "0"
                              },
                              {
                                "attrId": "2559554039",
                                "attrValue": "少甜",
                                "rank": 2,
                                "attrAddPrice": "0"
                              },
                              {
                                "attrId": "2559354772",
                                "attrValue": "少少甜",
                                "rank": 3,
                                "attrAddPrice": "0"
                              },
                              {
                                "attrId": "2559431388",
                                "attrValue": "微甜",
                                "rank": 4,
                                "attrAddPrice": "0"
                              },
                              {
                                "attrId": "2559455338",
                                "attrValue": "不另外加糖",
                                "rank": 5,
                                "attrAddPrice": "0"
                              }
                            ]
                          }
                        ],
                        "extendInfoMap": {},
                        "needQi": false
                      }
                    ],
                    "spuCategoryVOS": []
                  }
                ]
              },
              "isSupport": true,
              "dealUpperLimit": 100,
              "skuUpperLimit": 15
            },
            "mopProductPriceVO": {
              "currentPrice": "1490",
              "mopCurrentPrice": "null",
              "dealCurrentPrice": "1490",
              "discountPrice": "2010",
              "totalPrice": "3500",
              "selectNum": 1,
              "dealTotalPrice": "3500",
              "dealDiscountPrice": "2010",
              "needQi": false
            },
            "currentPage": 10,
            "usePromotionDetails": []
          }
        },
        "s": {
          "wrapCardStyle": {
            "position": "relative",
            "zIndex": 1
          }
        },
        "pc": {
          "mopTempCartTempProductList": {
            "r": true
          }
        },
        "e": {
          "e": {
            "onSubmitSuccess": [
              {
                "n": "BottomBar",
                "e": "onSubmitSuccess",
                "t": [
                  {
                    "t": "",
                    "f": ""
                  }
                ]
              }
            ]
          }
        }
      },
      "MopDataContainer": {
        "i": "430",
        "p": {
          "quantity": "1"
        },
        "s": {
          "wrapStyle": {
            "marginRight": 0,
            "marginLeft": 0
          }
        },
        "pc": {
          "quantity": {
            "r": true
          },
          "mopTempData": {
            "r": true
          }
        }
      },
      "AfterPay": {
        "i": "132",
        "t": "l",
        "p": {
          "afterPayList": [],
          "tailTips": [],
          "lx": {
            "channelName": "meishi",
            "pageInfoKey": "group-order-submit",
            "commonParams": {
              "is_mvp": "0",
              "deal_id": "1340587375",
              "poi_id": "1851844943",
              "tab_name": 0,
              "is_distribute": 0,
              "source": "-999",
              "scene_type": "1",
              "deal_sale_count": -999,
              "deal_count": "-999",
              "distribute_deal_count": -999,
              "bundle_product_source": 0,
              "page_version": "2",
              "page_module": "0",
              "has_text": 0,
              "submit_deal_info": "-999",
              "is_person_order_same_phone_number": 0,
              "is_person_login_same_phone_number": 0,
              "is_null": 1
            },
            "cid": "c_meishi_rao5v99i",
            "insurance_mc": {
              "bid": "b_meishi_h0kdj3z1_mc",
              "valLab": {
                "poi_id": "-999"
              }
            },
            "insurance_mv": {
              "bid": "b_meishi_h0kdj3z1_mv",
              "valLab": {
                "poi_id": "-999"
              }
            },
            "full_rebate_mv": {
              "bid": "b_meishi_hk57o0vx_mv",
              "valLab": {
                "activity_id": [],
                "page_version": "2"
              }
            },
            "full_rebate_mc": {
              "bid": "b_meishi_hk57o0vx_mc",
              "valLab": {
                "activity_id": [],
                "page_version": "2"
              }
            },
            "coupon_return_mv": {
              "bid": "b_meishi_vfisf00l_mv"
            }
          },
          "isTetuan": false
        },
        "s": {
          "cardWrapStyle": {
            "marginBottom": 0
          }
        },
        "pc": {
          "afterPayList": {
            "r": true
          }
        }
      },
      "BottomFill": {
        "i": "509",
        "t": "l",
        "p": {
          "full": false
        }
      },
      "DzBgLineargradient": {
        "i": "239",
        "t": "l",
        "p": {
          "start": {
            "x": 0,
            "y": 0
          },
          "end": {
            "x": 0,
            "y": 1
          },
          "colors": [
            "#FFFFFF",
            "#F4F4F4"
          ]
        },
        "s": {
          "wrapCardStyle": {
            "top": 43,
            "left": 0,
            "bottom": 0,
            "position": "absolute",
            "right": 0,
            "height": 150,
            "zIndex": 0
          }
        }
      },
      "MaxLeezCard": {
        "i": "37",
        "s": {
          "style": {
            "padding": 0,
            "margin": 0,
            "backgroundColor": "#f7f7f7",
            "paddingBottom": 0,
            "top": 0,
            "left": 0,
            "bottom": 0,
            "paddingRight": 0,
            "paddingTop": 0,
            "position": "absolute",
            "right": 0,
            "paddingLeft": 0
          }
        }
      },
      "MaxLeezCard1": {
        "i": "37",
        "s": {
          "style": {
            "padding": 0,
            "backgroundColor": "#ffffff",
            "right": 0,
            "borderRadius": 0,
            "left": 0,
            "height": 100
          }
        }
      },
      "DzBgLineargradient2": {
        "i": "239",
        "t": "l",
        "p": {
          "start": {
            "x": 0,
            "y": 0
          },
          "end": {
            "x": 0,
            "y": 1
          },
          "colors": [
            "#FFFFFF",
            "#F4F4F4"
          ]
        },
        "s": {
          "wrapCardStyle": {
            "position": "relative",
            "right": 0,
            "left": 0,
            "height": 100
          }
        }
      },
      "TopTag": {
        "i": "155",
        "t": "l",
        "p": {
          "labelList": [],
          "closeEmitKey": "CLOSE_POP_SLIDER_MODAL",
          "lx": {
            "channelName": "meishi",
            "pageInfoKey": "group-order-submit",
            "commonParams": {
              "is_mvp": "0",
              "deal_id": "1340587375",
              "poi_id": "1851844943",
              "tab_name": 0,
              "is_distribute": 0,
              "source": "-999",
              "scene_type": "1",
              "deal_sale_count": -999,
              "deal_count": "-999",
              "distribute_deal_count": -999,
              "bundle_product_source": 0,
              "page_version": "2",
              "page_module": "0",
              "has_text": 0,
              "submit_deal_info": "-999",
              "is_person_order_same_phone_number": 0,
              "is_person_login_same_phone_number": 0,
              "is_null": 1
            },
            "cid": "c_meishi_rao5v99i",
            "closeMc": {
              "bid": "b_meishi_byrm830y_mc"
            },
            "valLab": {
              "status": 0,
              "tab_name": "秒提·到店取",
              "deal_id": "1340587375",
              "poi_id": "1851844943",
              "mode_type": 2
            }
          },
          "labels": [],
          "closeVisible": true,
          "full": false
        },
        "s": {
          "wrapCardStyle": {
            "marginBottom": 13
          }
        }
      },
      "Dialog": {
        "i": "142",
        "t": "l",
        "p": {
          "reportTags": {
            "errCode": 0,
            "errMsg": "成功",
            "errUserMsg": "成功",
            "dpWX": false,
            "mtWX": false,
            "source": "food-poi",
            "routeByPortm": "0"
          },
          "isFoodPopBack": true,
          "lx": {
            "channelName": "meishi",
            "pageInfoKey": "group-order-submit",
            "commonParams": {
              "is_mvp": "0",
              "deal_id": "1340587375",
              "poi_id": "1851844943",
              "tab_name": 0,
              "is_distribute": 0,
              "source": "-999",
              "scene_type": "1",
              "deal_sale_count": -999,
              "deal_count": "-999",
              "distribute_deal_count": -999,
              "bundle_product_source": 0,
              "page_version": "2",
              "page_module": "0",
              "has_text": 0,
              "submit_deal_info": "-999",
              "is_person_order_same_phone_number": 0,
              "is_person_login_same_phone_number": 0,
              "is_null": 1
            },
            "cid": "c_meishi_rao5v99i",
            "module_mv": {
              "bid": "b_meishi_lvzq6i2d_mv"
            },
            "confirm_mc": {
              "bid": "b_meishi_zv9z65nj_mc"
            },
            "valLab": {
              "card_id": "",
              "title": "成功"
            }
          },
          "reportMsg": "",
          "scene": "food-order-submit-add"
        },
        "e": {
          "e": {
            "onReload": [
              {
                "n": "MeishiCommonDuoLifecycle1",
                "e": "update"
              }
            ]
          }
        }
      },
      "MeishiKaMopDuoSubmitRemindModal": {
        "i": "642",
        "p": {},
        "e": {
          "e": {
            "onReload": [
              {
                "n": "MeishiCommonDuoLifecycle1",
                "e": "update"
              }
            ]
          }
        }
      },
      "MeishiKaMopCheckShopModal": {
        "i": "403",
        "p": {
          "buyScene": "1",
          "pageQuery": {
            "mrn_transparent": "true",
            "mrn_biz": "meishi",
            "mrn_entry": "c-group-order-submit",
            "tabType": "5",
            "nibBizConsistency": "gmV2peeKZ5C2xJqoC9o14IlfIQJKqkO42Jf4ABsGz-8KD454ZUT648SFJb5Xmlo-W7hOiYrFcmjrzrm7sfnYubZN2_5zY5kTi2UrHKeoMvVrT5nT3t9GrhskJchFCoLwliEF1s34nZteNndoTq4p6jumFIat5E7x3OHWWfcsj4dLvGLpZX3OuprG5Z4aEmDaoMyq9sp2llHJnwzKWZ-JHeeaBOwWgg9awIgxp2w6d0M",
            "trafficSourceActivityId": "",
            "sec_source": "rhhj_dd",
            "isOnlyShowShopCart": "false",
            "mrn_component": "GroupOrderSubmit",
            "isDealJudge": "",
            "_referer": "food-poi",
            "flexibleJSON": "",
            "mrn_hideNextNavBar": "true",
            "hideLoading": "true",
            "groupBuyMopScene": "1",
            "hasKNBParams": "1",
            "venueId": "",
            "mlive_ext": "",
            "buyPoiIdEncrypt": "qB4r17707da606bc98ea64a037925971660ee8e63d7690a06106e1ce2a76ee607d88922f49ead8b8b2b7712a292610e43d2bac167cdcda7719f50f20vxu5",
            "source": "",
            "mrn_adjustParentFrame": "true",
            "productType": "",
            "dealId": "1340587375",
            "lng": "121.52897062950872",
            "halfScreenSubmitHeight": "0.85",
            "payPrice": "14.9",
            "showPrice": "14.9",
            "shelfFusion": "true",
            "lat": "31.273660438522672",
            "dd_source": "",
            "mrn_hideloading": "true",
            "govPromotion": "",
            "isTransparent": "true",
            "buyPoiId": "1851844943",
            "mrn_min_version": "2.115.0",
            "campaignId": ""
          },
          "chooseShopUrl": "imeituan://www.meituan.com/mrn?mrn_biz=meishi&mrn_entry=ka-mop-poi-select&mrn_component=kaMopPoiSelect&dishSource=10&shopId=1851844943&dealId=1340587375&brandId=288&jumpToShopSelectPageOnLoad=true&pageSource=instant-order-page",
          "disableSwitchShop": false,
          "location": {
            "lat": "31.273660438522672",
            "lng": "121.52897062950872",
            "accuracy": "7.230641488784651"
          },
          "isFromTetuan": false
        },
        "e": {
          "e": {
            "onSwitchShop": [
              {
                "n": "MeishiCommonDuoLifecycle1",
                "e": "update"
              }
            ],
            "onConfirmOrder": [
              {
                "n": "BottomBar",
                "e": "onMiaoTiSubmitPress",
                "t": [
                  {
                    "t": "miaoTiConfirm",
                    "f": ""
                  }
                ]
              }
            ]
          }
        }
      },
      "SubmitRisk": {
        "i": "192",
        "p": {
          "yodaEnv": "Prod",
          "lx": [],
          "yodaRequestParams": {
            "os": "ios",
            "platform": "mt",
            "version": "12.56.200",
            "uuid": "00000000000007A0030108A0C430C88DF8E7BA59BF348A177457840783633080",
            "userId": "3842765890",
            "token": "AgFsIpe7YXQee_IBR4ln-oXXq_F6jtq2AOMT_6oEuvwbZm3IQkWpq9RK7ZiTZb-EXRonInIFDWyzYAAAAAAENAAA2w_Qkp6xP7nbBz0_CIKZwutJA8YJUz3UHNqjoIPrlkhqnK4I_I3ifwXnnfUT-7KV"
          }
        },
        "e": {
          "e": {
            "onSurePress": [
              {
                "n": "BottomBar",
                "e": "onSubmitPress",
                "t": [
                  {
                    "t": "sType",
                    "f": ""
                  }
                ]
              }
            ]
          }
        }
      },
      "MeishiFoodGroupSubmitLogic": {
        "i": "248",
        "p": {
          "dealId": "1340587375",
          "CID": "c_meishi_rao5v99i"
        }
      },
      "FoodSubmitStatic": {
        "i": "1090"
      },
      "MeishiCommonDuoLifecycle1": {
        "i": "13",
        "e": {
          "e": {
            "preview.onEngineFail": [
              {
                "n": "FoodSubmitStatic",
                "e": "onPreviewEngineFail"
              }
            ],
            "preview.onResponse": [
              {
                "n": "FoodSubmitStatic",
                "e": "onPreviewResponse"
              }
            ],
            "submit.onFail": [
              {
                "n": "SubmitRisk",
                "e": "onRiskDialogShow",
                "t": [
                  {
                    "t": "item",
                    "f": "item"
                  }
                ]
              }
            ],
            "preview.onSuccess": [
              {
                "n": "MeishiCommonEventNav1",
                "e": "setWebDocumentTitle",
                "p": {
                  "title": "提交订单"
                }
              }
            ]
          }
        }
      },
      "MeishiCommonEventNav1": {
        "i": "90"
      },
      "MeishiUtilAutoReporterInstance1": {
        "i": "91"
      },
      "MeishiCommonEventLx1": {
        "i": "16"
      }
    },
    "currentData": {
      "poiName": "瑞幸咖啡（互联宝地二期店）"
    },
    "minifyHttpResponse": 1
  },
  "bizReq": {
    "bizCode": "nib.food.groupbuy",
    "environmentParam": {
      "duoCommonParam": {
        "location": {
          "lat": "31.273660438522672",
          "lng": "121.52897062950872",
          "accuracy": "7.230641488784651"
        },
        "userInfo": {
          "userId": "3842765890",
          "token": "AgFsIpe7YXQee_IBR4ln-oXXq_F6jtq2AOMT_6oEuvwbZm3IQkWpq9RK7ZiTZb-EXRonInIFDWyzYAAAAAAENAAA2w_Qkp6xP7nbBz0_CIKZwutJA8YJUz3UHNqjoIPrlkhqnK4I_I3ifwXnnfUT-7KV",
          "uuid": "00000000000007A0030108A0C430C88DF8E7BA59BF348A177457840783633080",
          "uuidV2": "00000000000007A0030108A0C430C88DF8E7BA59BF348A177457840783633080",
          "mtuuid": "00000000000007A0030108A0C430C88DF8E7BA59BF348A177457840783633080",
          "userAgent": "com.meituan.imeituan-beta/318515 (unknown, iOS 26.3.1, iPhone, Scale/3.000000)",
          "userIp": "203.76.219.237",
          "userIpV2": "103.202.145.196",
          "unionId": "8b854f09f2814f2cb120f473ac3930eea176350111025506278",
          "dpid": "",
          "regionId": "1000330700"
        },
        "cityInfo": {
          "cityId": "10",
          "locCityId": "10"
        },
        "systemInfo": {
          "version": "12.56.200",
          "systemVersion": "26.3.1",
          "device": "",
          "platform": "ios",
          "isWeb": false,
          "isWeChatMiniProgram": false,
          "isDebug": false,
          "isMRN": true,
          "mpAppId": "",
          "envInWeb": {},
          "utmInfo": {
            "source": "Alpha",
            "medium": "iphone",
            "term": "12.56.200",
            "content": "00000000000007A0030108A0C430C88DF8E7BA59BF348A177457840783633080",
            "campaign": "AgroupBgroupD200Ghomepage_searchH0"
          },
          "mpAppVersion": "",
          "mpPluginAppId": "",
          "mtgsig": {
            "a0": "3.0",
            "a1": "bb459669-615c-4dcd-a201-8dc32aa1b5e4",
            "a3": 25,
            "a4": 1777023661,
            "a5": "webgNQ5wqKvP4VZQcr7vHFJsXStXXJF01We0IXeV447BocrG4s4rQMHmEhNNqu4GLst3duJ7x03yZWtk+pQSDAW7jvS0Fn3jRQjgKxyTfT4nz2xKXVAW/axduMiTNZdwFeexvwFHcikCXMe6/p6v7gMcJX37tdvL4/fE+D45TNErpMlswlIIMEcr+QDfY4fUf6WYrvZ/2wkgbfvHiLsqsS1IRhgjZi1bGBKnZTZWokzi/WMJcIxKIwi9sLlhu2LDiYMTkG6VQ/im7iZt4fgQH9LqfOYBiaaeFlfl5LE8gwL3Ez+kiflsTY0HqwznlOtnvLFn71u6ddhQ/6Fyqodj5fg3ExYJikZ+e0uN9yhdssSxIN1FADsYWg7K+0RewUE/DCKX+XXIvIQMKRw=",
            "a6": 0,
            "a7": "Nd4AWv4k0Fx0fpkpQ5vyLWJvwRn2izg1Ny1qe09UlJFKrLcc2tsxUqx4d3eG57Xkb2m7z+hX/hdHVooBtZn3Gbl/hBI/W/v7d+hpgBVFl7M=",
            "a8": "5395074119b4b9a92eaca0858e8c71ddf177f128cf6ee8e411d4f76a",
            "a9": "fc9523c2MbB7W3R9uBkZRBgB4Q5MlhBLH1MNBNSxdr/PXCzCWtL3VNJeEB5h1Kh/7hoktPqbWATIxb5zyNxnkVEB1C2QlyXoDwtZ2L3OC2X1AwiNB9xBDX2Aihm6/rjPETQrOYnfola/VM5rk+tVsWNw2VNoNb9Po5pPWdB1SMIJl11jgiiOaDzJSRZaa81kkzxaSnZtHjH6KPcOo82NnoDxvOMxacdG1INzcep3KQQGfv/N2UOven0uO3wFqWkqNjTxOcIH1z2fFHiRiUtAzlz7984sDUUcyqtljAWiPfTrujwtHmJyDUOdm/FzJOt+xrLeKGAQ4qS9qXOmiNOp2GVn7gd/G4g6i9D7fv/dvgrBBaobr8w6KBGnBPbQWFIw2Kz8JzY/Ri4UTm+tSDhw7Y9yKtUV7pInJy8pxbjmqDcv1d8EqjV82z13r9kpTjY712QDyQcTNEnIcs/lB9/RDTYfNzswcXWW3OXTRTqnEul0wAdHbenlUItWsCcVzdbyecT+Dp5cyjetpKF9TUL0fHHbLWqdBW0Ic6CGOkfBh4rlt7GoNKC5FTDMXpvbEhycnIUMaalgTSJ9WqgtKvpSbzYdYBu0tiNPWQ4T9xa7+aNWl7+XocezI2Y+z+B9voIj9uI19FrBM9jFVQd9AjVWj6qLhqu0fIavU4CJZmNUz2Yg/aZHoc3yWKYmX8gf3c+Gm8w5Kp2m",
            "a10": "5,202,1.1.6",
            "x0": 2,
            "a2": "4ab34a37690e9b4cb072bd4ea6c0a7fa"
          },
          "is_HOTEL": false,
          "is_DP": false,
          "is_MT": true
        },
        "fingerprint": {
          "fingerprint": ""
        },
        "storage": {}
      },
      "submitVersion": "12.31.000",
      "pageId": 0,
      "gpsCoordinateType": "GCJ02",
      "magicMemberComponentVersion": "0.3.0"
    },
    "productParam": {
      "productId": "1340587375",
      "quantity": 1
    },
    "poiParam": {
      "poiId": "1851844943"
    },
    "merchantMemberParam": {
      "forcePut": 1
    },
    "payParam": {
      "payType": 0,
      "cashierEnvParam": {}
    },
    "promoParam": {
      "operatorPromoType": "0",
      "queryPromoLimitType": 0
    },
    "riskParam": {
      "erasePromotionType": 0,
      "yodaInfo": {}
    },
    "pageUrl": {
      "mrn_transparent": "true",
      "mrn_biz": "meishi",
      "mrn_entry": "c-group-order-submit",
      "tabType": "5",
      "nibBizConsistency": "gmV2peeKZ5C2xJqoC9o14IlfIQJKqkO42Jf4ABsGz-8KD454ZUT648SFJb5Xmlo-W7hOiYrFcmjrzrm7sfnYubZN2_5zY5kTi2UrHKeoMvVrT5nT3t9GrhskJchFCoLwliEF1s34nZteNndoTq4p6jumFIat5E7x3OHWWfcsj4dLvGLpZX3OuprG5Z4aEmDaoMyq9sp2llHJnwzKWZ-JHeeaBOwWgg9awIgxp2w6d0M",
      "trafficSourceActivityId": "",
      "sec_source": "rhhj_dd",
      "isOnlyShowShopCart": "false",
      "mrn_component": "GroupOrderSubmit",
      "isDealJudge": "",
      "_referer": "food-poi",
      "flexibleJSON": "",
      "mrn_hideNextNavBar": "true",
      "hideLoading": "true",
      "groupBuyMopScene": "1",
      "hasKNBParams": "1",
      "venueId": "",
      "mlive_ext": "",
      "buyPoiIdEncrypt": "qB4r17707da606bc98ea64a037925971660ee8e63d7690a06106e1ce2a76ee607d88922f49ead8b8b2b7712a292610e43d2bac167cdcda7719f50f20vxu5",
      "source": "",
      "mrn_adjustParentFrame": "true",
      "productType": "",
      "dealId": "1340587375",
      "lng": "121.52897062950872",
      "halfScreenSubmitHeight": "0.85",
      "payPrice": "14.9",
      "showPrice": "14.9",
      "shelfFusion": "true",
      "lat": "31.273660438522672",
      "dd_source": "",
      "mrn_hideloading": "true",
      "govPromotion": "",
      "isTransparent": "true",
      "buyPoiId": "1851844943",
      "mrn_min_version": "2.115.0",
      "campaignId": ""
    },
    "bizExtend": {},
    "userAgreementParam": {
      "agreementInfoList": []
    },
    "pageSceneParam": {
      "pageScene": 0,
      "nextPageScene": 0,
      "promotionPosition": "2109",
      "inflatePosition": "2140",
      "pageTraceInfo": [
        "2026-04-24 17:41:01 doBizPreview   -   3668242131246972301"
      ],
      "submitBtnStatus": 0,
      "openSelectCouponPageFlag": false,
      "giftIntention": 0,
      "pageSourceId": 0
    },
    "createPriceParam": {},
    "transferDataParam": {
      "transferData": {
        "quantity": "1"
      }
    },
    "operateTypeParam": {
      "operateType": 0
    },
    "cartParam": {
      "promoParamMap": {}
    },
    "diff": false
  },
  "bizRes": {
    "code": 0,
    "message": "成功",
    "userMessage": "成功",
    "data": {
      "abTestVOList": [
        {
          "key": "ab_group_QDJBH",
          "douHuTestConfigVOList": [],
          "horizonTestConfigVOList": [
            {
              "expKey": "ab_group_QDJBH",
              "expResult": true
            }
          ],
          "arenaTestConfigVOList": []
        }
      ],
      "bizResultCode": 0,
      "pageSceneParamVO": {
        "pageScene": 5,
        "nextPageScene": 0,
        "promotionPosition": "2109",
        "pageTraceInfo": [
          "2026-04-24 17:41:01 doBizPreview   -   3668242131246972301"
        ],
        "tabInfoVO": [
          {
            "pageScene": 5,
            "tabTitle": "秒提·到店取",
            "tabTag": "3",
            "tabStyle": 0
          },
          {
            "pageScene": 1,
            "tabTitle": "买团购",
            "tabTag": "3",
            "tabStyle": 0
          }
        ],
        "submitBtnStatus": 0,
        "multiTabScene": 1,
        "switchTabType": 1,
        "backPrePageType": 1,
        "openSelectCouponPageFlag": false,
        "giftIntention": 0,
        "pageSourceId": 0
      },
      "preOrderExtParams": "",
      "afterPayInfoVO": {
        "afterPayList": []
      },
      "mopPreOrderVO": {
        "mopShopInfoVO": {
          "shopId": "1851844943",
          "shopIcon": "<https://p0.meituan.net/40.40/travelcube/7b5cf1381d1f3c7e1d0896a84dcc56c627952.jpg>",
          "shopName": "瑞幸咖啡（互联宝地二期店）",
          "shopAddress": "杨浦区黄兴路221号互联宝地二期负1层B1-68",
          "chooseShopUrl": "imeituan://www.meituan.com/mrn?mrn_biz=meishi&mrn_entry=ka-mop-poi-select&mrn_component=kaMopPoiSelect&dishSource=10&shopId=1851844943&dealId=1340587375&brandId=288&jumpToShopSelectPageOnLoad=true&pageSource=instant-order-page",
          "distance": 228,
          "distanceDesc": "228m",
          "brandId": "288",
          "topTipList": [
            {
              "content": "附近有多家门店，请确认是否在本店取餐",
              "type": 0
            }
          ],
          "bottomTipList": [],
          "topTipRichTextList": [
            {
              "content": "<span style='color: #888888;'>距您228m，杨浦区黄兴路221号互联宝地二期负1层B1-68</span>",
              "type": 0
            },
            {
              "content": "<span style='color: #888888;'>附近有<span style='color: #FF4B10;'>多家门店</span>，请确认取餐门店</span>",
              "type": 0
            }
          ],
          "tipList": []
        },
        "mopBrandInfoVO": {
          "brandId": "288",
          "mopBrandType": 20
        },
        "mopDealMappingInfoVO": {
          "mopDealMappingProductInfoVO": {
            "dealId": 1340587375,
            "dealIdStr": "1340587375",
            "dealTag": 1,
            "dealName": "【耶加系列】3选1",
            "mappingId": "66081150",
            "dealMappingType": 20,
            "dealMappingChooseType": 3,
            "mopDealProductGroupList": [
              {
                "groupName": "品质SOE系列 3选1",
                "groupId": 84047472,
                "maxChoiceNum": 1,
                "minChoiceNum": 1,
                "canRepeatChoose": true,
                "mopProductList": [
                  {
                    "spuName": "耶加雪菲美式",
                    "spuId": "840897641",
                    "isAvailable": true,
                    "spuPicAddr": "<https://img.meituan.net/shopdirectconnectpic/3f907c6abc2c55da04e5c1f7ba785ddc.jpg>",
                    "defaultSkuId": "2878743098",
                    "mopSkuList": [
                      {
                        "skuId": "2878743098",
                        "spuId": "840897641",
                        "skuName": "小黑杯",
                        "isAvailable": true,
                        "isSupplementSku": false,
                        "currentPrice": "2900",
                        "originalPrice": "2900",
                        "addPrice": "0",
                        "stockCount": -1,
                        "mopSkuSaleAttrList": [
                          {
                            "groupCode": "64",
                            "attributeId": "416241906"
                          }
                        ],
                        "mopCustomRuleList": [
                          {
                            "premiumGroupCode": "17",
                            "defaultSelect": true,
                            "mustSelect": true,
                            "maxChoice": 1,
                            "minChoice": 1,
                            "defaultSelectNum": 1,
                            "unitPerStep": 1,
                            "exchange": false,
                            "hide": false,
                            "fold": false,
                            "rank": 1,
                            "ruleType": 10,
                            "multiChoice": false,
                            "groupMultiChoice": false
                          },
                          {
                            "premiumGroupCode": "14",
                            "defaultSelect": true,
                            "mustSelect": true,
                            "maxChoice": 1,
                            "minChoice": 1,
                            "defaultSelectNum": 1,
                            "unitPerStep": 1,
                            "exchange": false,
                            "hide": false,
                            "fold": false,
                            "rank": 2,
                            "ruleType": 10,
                            "multiChoice": false,
                            "groupMultiChoice": false
                          },
                          {
                            "premiumId": "2559254875",
                            "premiumGroupCode": "17",
                            "defaultSelect": false,
                            "mustSelect": false,
                            "maxChoice": 1,
                            "minChoice": 0,
                            "maxFreeNum": 0,
                            "defaultSelectNum": 1,
                            "unitPerStep": 1,
                            "exchange": false,
                            "hide": false,
                            "rank": 1,
                            "ruleType": 20,
                            "multiChoice": false,
                            "groupMultiChoice": false,
                            "price": "0",
                            "premiumName": "冰"
                          },
                          {
                            "premiumId": "2559371838",
                            "premiumGroupCode": "14",
                            "defaultSelect": false,
                            "mustSelect": false,
                            "maxChoice": 1,
                            "minChoice": 0,
                            "maxFreeNum": 0,
                            "defaultSelectNum": 1,
                            "unitPerStep": 1,
                            "exchange": false,
                            "hide": false,
                            "rank": 1,
                            "ruleType": 20,
                            "multiChoice": false,
                            "groupMultiChoice": false,
                            "price": "0",
                            "premiumName": "标准甜"
                          },
                          {
                            "premiumId": "2559322629",
                            "premiumGroupCode": "17",
                            "defaultSelect": true,
                            "mustSelect": false,
                            "maxChoice": 1,
                            "minChoice": 0,
                            "maxFreeNum": 0,
                            "defaultSelectNum": 1,
                            "unitPerStep": 1,
                            "exchange": false,
                            "hide": false,
                            "rank": 2,
                            "ruleType": 20,
                            "multiChoice": false,
                            "groupMultiChoice": false,
                            "price": "0",
                            "premiumName": "热"
                          },
                          {
                            "premiumId": "2559393711",
                            "premiumGroupCode": "14",
                            "defaultSelect": false,
                            "mustSelect": false,
                            "maxChoice": 1,
                            "minChoice": 0,
                            "maxFreeNum": 0,
                            "defaultSelectNum": 1,
                            "unitPerStep": 1,
                            "exchange": false,
                            "hide": false,
                            "rank": 2,
                            "ruleType": 20,
                            "multiChoice": false,
                            "groupMultiChoice": false,
                            "price": "0",
                            "premiumName": "少甜"
                          },
                          {
                            "premiumId": "2559354186",
                            "premiumGroupCode": "14",
                            "defaultSelect": false,
                            "mustSelect": false,
                            "maxChoice": 1,
                            "minChoice": 0,
                            "maxFreeNum": 0,
                            "defaultSelectNum": 1,
                            "unitPerStep": 1,
                            "exchange": false,
                            "hide": false,
                            "rank": 3,
                            "ruleType": 20,
                            "multiChoice": false,
                            "groupMultiChoice": false,
                            "price": "0",
                            "premiumName": "少少甜"
                          },
                          {
                            "premiumId": "2559380169",
                            "premiumGroupCode": "14",
                            "defaultSelect": false,
                            "mustSelect": false,
                            "maxChoice": 1,
                            "minChoice": 0,
                            "maxFreeNum": 0,
                            "defaultSelectNum": 1,
                            "unitPerStep": 1,
                            "exchange": false,
                            "hide": false,
                            "rank": 4,
                            "ruleType": 20,
                            "multiChoice": false,
                            "groupMultiChoice": false,
                            "price": "0",
                            "premiumName": "微甜"
                          },
                          {
                            "premiumId": "2559418501",
                            "premiumGroupCode": "14",
                            "defaultSelect": true,
                            "mustSelect": false,
                            "maxChoice": 1,
                            "minChoice": 0,
                            "maxFreeNum": 0,
                            "defaultSelectNum": 1,
                            "unitPerStep": 1,
                            "exchange": false,
                            "hide": false,
                            "rank": 5,
                            "ruleType": 20,
                            "multiChoice": false,
                            "groupMultiChoice": false,
                            "price": "0",
                            "premiumName": "不另外加糖"
                          }
                        ]
                      }
                    ],
                    "mopProductAttrGroups": [
                      {
                        "groupName": "杯型",
                        "groupCode": "64",
                        "maxChoiceNum": 1,
                        "minChoiceNum": 1,
                        "isSellAttributeGroup": true,
                        "rank": 1,
                        "mopProductAttrItems": [
                          {
                            "attrId": "416241906",
                            "attrValue": "小黑杯",
                            "rank": 1,
                            "attrAddPrice": "0"
                          }
                        ]
                      },
                      {
                        "groupName": "温度",
                        "groupCode": "17",
                        "isSellAttributeGroup": false,
                        "multiChoice": false,
                        "chooseMultiPremium": false,
                        "rank": 1,
                        "mopProductAttrItems": [
                          {
                            "attrId": "2559254875",
                            "attrValue": "冰",
                            "rank": 1,
                            "attrAddPrice": "0"
                          },
                          {
                            "attrId": "2559322629",
                            "attrValue": "热",
                            "rank": 2,
                            "attrAddPrice": "0"
                          }
                        ]
                      },
                      {
                        "groupName": "糖",
                        "groupCode": "14",
                        "isSellAttributeGroup": false,
                        "multiChoice": false,
                        "chooseMultiPremium": false,
                        "rank": 2,
                        "mopProductAttrItems": [
                          {
                            "attrId": "2559371838",
                            "attrValue": "标准甜",
                            "rank": 1,
                            "attrAddPrice": "0"
                          },
                          {
                            "attrId": "2559393711",
                            "attrValue": "少甜",
                            "rank": 2,
                            "attrAddPrice": "0"
                          },
                          {
                            "attrId": "2559354186",
                            "attrValue": "少少甜",
                            "rank": 3,
                            "attrAddPrice": "0"
                          },
                          {
                            "attrId": "2559380169",
                            "attrValue": "微甜",
                            "rank": 4,
                            "attrAddPrice": "0"
                          },
                          {
                            "attrId": "2559418501",
                            "attrValue": "不另外加糖",
                            "rank": 5,
                            "attrAddPrice": "0"
                          }
                        ]
                      }
                    ],
                    "extendInfoMap": {},
                    "needQi": false
                  },
                  {
                    "spuName": "耶加雪菲拿铁",
                    "spuId": "840838517",
                    "isAvailable": true,
                    "spuPicAddr": "<https://img.meituan.net/shopdirectconnectpic/1dc2160099934ae0f02ac5b9050e502e.jpg>",
                    "defaultSkuId": "2878699915",
                    "mopSkuList": [
                      {
                        "skuId": "2878699915",
                        "spuId": "840838517",
                        "skuName": "小黑杯",
                        "isAvailable": true,
                        "isSupplementSku": false,
                        "currentPrice": "3200",
                        "originalPrice": "3200",
                        "addPrice": "0",
                        "stockCount": -1,
                        "mopSkuSaleAttrList": [
                          {
                            "groupCode": "64",
                            "attributeId": "416245679"
                          }
                        ],
                        "mopCustomRuleList": [
                          {
                            "premiumGroupCode": "17",
                            "defaultSelect": true,
                            "mustSelect": true,
                            "maxChoice": 1,
                            "minChoice": 1,
                            "defaultSelectNum": 1,
                            "unitPerStep": 1,
                            "exchange": false,
                            "hide": false,
                            "fold": false,
                            "rank": 1,
                            "ruleType": 10,
                            "multiChoice": false,
                            "groupMultiChoice": false
                          },
                          {
                            "premiumGroupCode": "14",
                            "defaultSelect": true,
                            "mustSelect": true,
                            "maxChoice": 1,
                            "minChoice": 1,
                            "defaultSelectNum": 1,
                            "unitPerStep": 1,
                            "exchange": false,
                            "hide": false,
                            "fold": false,
                            "rank": 2,
                            "ruleType": 10,
                            "multiChoice": false,
                            "groupMultiChoice": false
                          },
                          {
                            "premiumGroupCode": "102",
                            "defaultSelect": true,
                            "mustSelect": true,
                            "maxChoice": 1,
                            "minChoice": 1,
                            "defaultSelectNum": 1,
                            "unitPerStep": 1,
                            "exchange": false,
                            "hide": false,
                            "fold": false,
                            "rank": 3,
                            "ruleType": 10,
                            "multiChoice": false,
                            "groupMultiChoice": false
                          },
                          {
                            "premiumId": "2559417450",
                            "premiumGroupCode": "17",
                            "defaultSelect": false,
                            "mustSelect": false,
                            "maxChoice": 1,
                            "minChoice": 0,
                            "maxFreeNum": 0,
                            "defaultSelectNum": 1,
                            "unitPerStep": 1,
                            "exchange": false,
                            "hide": false,
                            "rank": 1,
                            "ruleType": 20,
                            "multiChoice": false,
                            "groupMultiChoice": false,
                            "price": "0",
                            "premiumName": "冰"
                          },
                          {
                            "premiumId": "2559477542",
                            "premiumGroupCode": "14",
                            "defaultSelect": false,
                            "mustSelect": false,
                            "maxChoice": 1,
                            "minChoice": 0,
                            "maxFreeNum": 0,
                            "defaultSelectNum": 1,
                            "unitPerStep": 1,
                            "exchange": false,
                            "hide": false,
                            "rank": 1,
                            "ruleType": 20,
                            "multiChoice": false,
                            "groupMultiChoice": false,
                            "price": "0",
                            "premiumName": "标准甜"
                          },
                          {
                            "premiumId": "2559424294",
                            "premiumGroupCode": "102",
                            "defaultSelect": true,
                            "mustSelect": false,
                            "maxChoice": 1,
                            "minChoice": 0,
                            "maxFreeNum": 0,
                            "defaultSelectNum": 1,
                            "unitPerStep": 1,
                            "exchange": false,
                            "hide": false,
                            "rank": 1,
                            "ruleType": 20,
                            "multiChoice": false,
                            "groupMultiChoice": false,
                            "price": "0",
                            "premiumName": "牛奶"
                          },
                          {
                            "premiumId": "2559523243",
                            "premiumGroupCode": "17",
                            "defaultSelect": true,
                            "mustSelect": false,
                            "maxChoice": 1,
                            "minChoice": 0,
                            "maxFreeNum": 0,
                            "defaultSelectNum": 1,
                            "unitPerStep": 1,
                            "exchange": false,
                            "hide": false,
                            "rank": 2,
                            "ruleType": 20,
                            "multiChoice": false,
                            "groupMultiChoice": false,
                            "price": "0",
                            "premiumName": "热"
                          },
                          {
                            "premiumId": "2559475737",
                            "premiumGroupCode": "14",
                            "defaultSelect": false,
                            "mustSelect": false,
                            "maxChoice": 1,
                            "minChoice": 0,
                            "maxFreeNum": 0,
                            "defaultSelectNum": 1,
                            "unitPerStep": 1,
                            "exchange": false,
                            "hide": false,
                            "rank": 2,
                            "ruleType": 20,
                            "multiChoice": false,
                            "groupMultiChoice": false,
                            "price": "0",
                            "premiumName": "少甜"
                          },
                          {
                            "premiumId": "2559411529",
                            "premiumGroupCode": "14",
                            "defaultSelect": false,
                            "mustSelect": false,
                            "maxChoice": 1,
                            "minChoice": 0,
                            "maxFreeNum": 0,
                            "defaultSelectNum": 1,
                            "unitPerStep": 1,
                            "exchange": false,
                            "hide": false,
                            "rank": 3,
                            "ruleType": 20,
                            "multiChoice": false,
                            "groupMultiChoice": false,
                            "price": "0",
                            "premiumName": "少少甜"
                          },
                          {
                            "premiumId": "2559398627",
                            "premiumGroupCode": "14",
                            "defaultSelect": false,
                            "mustSelect": false,
                            "maxChoice": 1,
                            "minChoice": 0,
                            "maxFreeNum": 0,
                            "defaultSelectNum": 1,
                            "unitPerStep": 1,
                            "exchange": false,
                            "hide": false,
                            "rank": 4,
                            "ruleType": 20,
                            "multiChoice": false,
                            "groupMultiChoice": false,
                            "price": "0",
                            "premiumName": "微甜"
                          },
                          {
                            "premiumId": "2559452808",
                            "premiumGroupCode": "14",
                            "defaultSelect": true,
                            "mustSelect": false,
                            "maxChoice": 1,
                            "minChoice": 0,
                            "maxFreeNum": 0,
                            "defaultSelectNum": 1,
                            "unitPerStep": 1,
                            "exchange": false,
                            "hide": false,
                            "rank": 5,
                            "ruleType": 20,
                            "multiChoice": false,
                            "groupMultiChoice": false,
                            "price": "0",
                            "premiumName": "不另外加糖"
                          }
                        ]
                      }
                    ],
                    "mopProductAttrGroups": [
                      {
                        "groupName": "杯型",
                        "groupCode": "64",
                        "maxChoiceNum": 1,
                        "minChoiceNum": 1,
                        "isSellAttributeGroup": true,
                        "rank": 1,
                        "mopProductAttrItems": [
                          {
                            "attrId": "416245679",
                            "attrValue": "小黑杯",
                            "rank": 1,
                            "attrAddPrice": "0"
                          }
                        ]
                      },
                      {
                        "groupName": "温度",
                        "groupCode": "17",
                        "isSellAttributeGroup": false,
                        "multiChoice": false,
                        "chooseMultiPremium": false,
                        "rank": 1,
                        "mopProductAttrItems": [
                          {
                            "attrId": "2559417450",
                            "attrValue": "冰",
                            "rank": 1,
                            "attrAddPrice": "0"
                          },
                          {
                            "attrId": "2559523243",
                            "attrValue": "热",
                            "rank": 2,
                            "attrAddPrice": "0"
                          }
                        ]
                      },
                      {
                        "groupName": "糖",
                        "groupCode": "14",
                        "isSellAttributeGroup": false,
                        "multiChoice": false,
                        "chooseMultiPremium": false,
                        "rank": 2,
                        "mopProductAttrItems": [
                          {
                            "attrId": "2559477542",
                            "attrValue": "标准甜",
                            "rank": 1,
                            "attrAddPrice": "0"
                          },
                          {
                            "attrId": "2559475737",
                            "attrValue": "少甜",
                            "rank": 2,
                            "attrAddPrice": "0"
                          },
                          {
                            "attrId": "2559411529",
                            "attrValue": "少少甜",
                            "rank": 3,
                            "attrAddPrice": "0"
                          },
                          {
                            "attrId": "2559398627",
                            "attrValue": "微甜",
                            "rank": 4,
                            "attrAddPrice": "0"
                          },
                          {
                            "attrId": "2559452808",
                            "attrValue": "不另外加糖",
                            "rank": 5,
                            "attrAddPrice": "0"
                          }
                        ]
                      },
                      {
                        "groupName": "奶基",
                        "groupCode": "102",
                        "isSellAttributeGroup": false,
                        "multiChoice": false,
                        "chooseMultiPremium": false,
                        "rank": 3,
                        "mopProductAttrItems": [
                          {
                            "attrId": "2559424294",
                            "attrValue": "牛奶",
                            "rank": 1,
                            "attrAddPrice": "0"
                          }
                        ]
                      }
                    ],
                    "extendInfoMap": {},
                    "needQi": false
                  },
                  {
                    "spuName": "耶加雪菲·澳瑞白",
                    "spuId": "840928420",
                    "isAvailable": true,
                    "spuPicAddr": "<https://img.meituan.net/shopdirectconnectpic/e28b7c7c5ba91185a42a904542f69678.jpg>",
                    "defaultSkuId": "2878738635",
                    "mopSkuList": [
                      {
                        "skuId": "2878738635",
                        "spuId": "840928420",
                        "skuName": "小黑杯",
                        "isAvailable": true,
                        "isSupplementSku": false,
                        "currentPrice": "3500",
                        "originalPrice": "3500",
                        "addPrice": "0",
                        "stockCount": -1,
                        "mopSkuSaleAttrList": [
                          {
                            "groupCode": "64",
                            "attributeId": "416270475"
                          }
                        ],
                        "mopCustomRuleList": [
                          {
                            "premiumGroupCode": "17",
                            "defaultSelect": true,
                            "mustSelect": true,
                            "maxChoice": 1,
                            "minChoice": 1,
                            "defaultSelectNum": 1,
                            "unitPerStep": 1,
                            "exchange": false,
                            "hide": false,
                            "fold": false,
                            "rank": 1,
                            "ruleType": 10,
                            "multiChoice": false,
                            "groupMultiChoice": false
                          },
                          {
                            "premiumGroupCode": "14",
                            "defaultSelect": true,
                            "mustSelect": true,
                            "maxChoice": 1,
                            "minChoice": 1,
                            "defaultSelectNum": 1,
                            "unitPerStep": 1,
                            "exchange": false,
                            "hide": false,
                            "fold": false,
                            "rank": 2,
                            "ruleType": 10,
                            "multiChoice": false,
                            "groupMultiChoice": false
                          },
                          {
                            "premiumId": "2559464094",
                            "premiumGroupCode": "17",
                            "defaultSelect": false,
                            "mustSelect": false,
                            "maxChoice": 1,
                            "minChoice": 0,
                            "maxFreeNum": 0,
                            "defaultSelectNum": 1,
                            "unitPerStep": 1,
                            "exchange": false,
                            "hide": false,
                            "rank": 1,
                            "ruleType": 20,
                            "multiChoice": false,
                            "groupMultiChoice": false,
                            "price": "0",
                            "premiumName": "冰"
                          },
                          {
                            "premiumId": "2559496038",
                            "premiumGroupCode": "14",
                            "defaultSelect": false,
                            "mustSelect": false,
                            "maxChoice": 1,
                            "minChoice": 0,
                            "maxFreeNum": 0,
                            "defaultSelectNum": 1,
                            "unitPerStep": 1,
                            "exchange": false,
                            "hide": false,
                            "rank": 1,
                            "ruleType": 20,
                            "multiChoice": false,
                            "groupMultiChoice": false,
                            "price": "0",
                            "premiumName": "标准甜"
                          },
                          {
                            "premiumId": "2559409759",
                            "premiumGroupCode": "17",
                            "defaultSelect": true,
                            "mustSelect": false,
                            "maxChoice": 1,
                            "minChoice": 0,
                            "maxFreeNum": 0,
                            "defaultSelectNum": 1,
                            "unitPerStep": 1,
                            "exchange": false,
                            "hide": false,
                            "rank": 2,
                            "ruleType": 20,
                            "multiChoice": false,
                            "groupMultiChoice": false,
                            "price": "0",
                            "premiumName": "热"
                          },
                          {
                            "premiumId": "2559554039",
                            "premiumGroupCode": "14",
                            "defaultSelect": false,
                            "mustSelect": false,
                            "maxChoice": 1,
                            "minChoice": 0,
                            "maxFreeNum": 0,
                            "defaultSelectNum": 1,
                            "unitPerStep": 1,
                            "exchange": false,
                            "hide": false,
                            "rank": 2,
                            "ruleType": 20,
                            "multiChoice": false,
                            "groupMultiChoice": false,
                            "price": "0",
                            "premiumName": "少甜"
                          },
                          {
                            "premiumId": "2559354772",
                            "premiumGroupCode": "14",
                            "defaultSelect": false,
                            "mustSelect": false,
                            "maxChoice": 1,
                            "minChoice": 0,
                            "maxFreeNum": 0,
                            "defaultSelectNum": 1,
                            "unitPerStep": 1,
                            "exchange": false,
                            "hide": false,
                            "rank": 3,
                            "ruleType": 20,
                            "multiChoice": false,
                            "groupMultiChoice": false,
                            "price": "0",
                            "premiumName": "少少甜"
                          },
                          {
                            "premiumId": "2559431388",
                            "premiumGroupCode": "14",
                            "defaultSelect": false,
                            "mustSelect": false,
                            "maxChoice": 1,
                            "minChoice": 0,
                            "maxFreeNum": 0,
                            "defaultSelectNum": 1,
                            "unitPerStep": 1,
                            "exchange": false,
                            "hide": false,
                            "rank": 4,
                            "ruleType": 20,
                            "multiChoice": false,
                            "groupMultiChoice": false,
                            "price": "0",
                            "premiumName": "微甜"
                          },
                          {
                            "premiumId": "2559455338",
                            "premiumGroupCode": "14",
                            "defaultSelect": true,
                            "mustSelect": false,
                            "maxChoice": 1,
                            "minChoice": 0,
                            "maxFreeNum": 0,
                            "defaultSelectNum": 1,
                            "unitPerStep": 1,
                            "exchange": false,
                            "hide": false,
                            "rank": 5,
                            "ruleType": 20,
                            "multiChoice": false,
                            "groupMultiChoice": false,
                            "price": "0",
                            "premiumName": "不另外加糖"
                          }
                        ]
                      }
                    ],
                    "mopProductAttrGroups": [
                      {
                        "groupName": "杯型",
                        "groupCode": "64",
                        "maxChoiceNum": 1,
                        "minChoiceNum": 1,
                        "isSellAttributeGroup": true,
                        "rank": 1,
                        "mopProductAttrItems": [
                          {
                            "attrId": "416270475",
                            "attrValue": "小黑杯",
                            "rank": 1,
                            "attrAddPrice": "0"
                          }
                        ]
                      },
                      {
                        "groupName": "温度",
                        "groupCode": "17",
                        "isSellAttributeGroup": false,
                        "multiChoice": false,
                        "chooseMultiPremium": false,
                        "rank": 1,
                        "mopProductAttrItems": [
                          {
                            "attrId": "2559464094",
                            "attrValue": "冰",
                            "rank": 1,
                            "attrAddPrice": "0"
                          },
                          {
                            "attrId": "2559409759",
                            "attrValue": "热",
                            "rank": 2,
                            "attrAddPrice": "0"
                          }
                        ]
                      },
                      {
                        "groupName": "糖",
                        "groupCode": "14",
                        "isSellAttributeGroup": false,
                        "multiChoice": false,
                        "chooseMultiPremium": false,
                        "rank": 2,
                        "mopProductAttrItems": [
                          {
                            "attrId": "2559496038",
                            "attrValue": "标准甜",
                            "rank": 1,
                            "attrAddPrice": "0"
                          },
                          {
                            "attrId": "2559554039",
                            "attrValue": "少甜",
                            "rank": 2,
                            "attrAddPrice": "0"
                          },
                          {
                            "attrId": "2559354772",
                            "attrValue": "少少甜",
                            "rank": 3,
                            "attrAddPrice": "0"
                          },
                          {
                            "attrId": "2559431388",
                            "attrValue": "微甜",
                            "rank": 4,
                            "attrAddPrice": "0"
                          },
                          {
                            "attrId": "2559455338",
                            "attrValue": "不另外加糖",
                            "rank": 5,
                            "attrAddPrice": "0"
                          }
                        ]
                      }
                    ],
                    "extendInfoMap": {},
                    "needQi": false
                  }
                ],
                "spuCategoryVOS": []
              }
            ]
          },
          "isSupport": true,
          "dealUpperLimit": 100,
          "skuUpperLimit": 15
        },
        "mopProductPriceVO": {
          "currentPrice": "1490",
          "mopCurrentPrice": "null",
          "dealCurrentPrice": "1490",
          "discountPrice": "2010",
          "totalPrice": "3500",
          "selectNum": 1,
          "dealTotalPrice": "3500",
          "dealDiscountPrice": "2010",
          "needQi": false
        },
        "currentPage": 10,
        "usePromotionDetails": []
      },
      "transferDataVO": {
        "transferData": {
          "quantity": "1"
        }
      },
      "giftInfoVO": {
        "canGive": false
      }
    },
    "success": true,
    "fail": false
  }
}
```

### 联名套餐响应

[image.png](https://km.sankuai.com/api/file/cdn/2759161502/234196325442?contentType=1&isNewContent=false)

### 完整响应

```
// 代码块
{
  "data": {
    "pageId": "12413",
    "pageProtocolId": "0350",
    "pageProtocolVersion": "0001",
    "bizRespStatus": {
      "isError": false,
      "errorToast": true,
      "extra": null
    },
    "struct": [
      {
        "n": "MeishiCommonDuoParams"
      },
      {
        "n": "TopBottomSlide",
        "s": {
          "renderModuleNodes": [
            {
              "n": "MeishiGroupBuyTab"
            },
            {
              "n": "MopContainer"
            },
            {
              "n": "MopDataContainer"
            },
            {
              "n": "AfterPay"
            },
            {
              "n": "BottomFill"
            }
          ],
          "renderTop": [
            {
              "n": "DzBgLineargradient"
            }
          ],
          "renderBackground": [
            {
              "n": "MaxLeezCard",
              "s": {
                "children": [
                  {
                    "n": "MaxLeezCard1"
                  },
                  {
                    "n": "DzBgLineargradient2"
                  }
                ]
              }
            }
          ],
          "renderTopChildren": [
            {
              "n": "TopTag"
            }
          ]
        }
      },
      {
        "n": "Dialog"
      },
      {
        "n": "MeishiKaMopDuoSubmitRemindModal"
      },
      {
        "n": "MeishiKaMopCheckShopModal"
      },
      {
        "n": "SubmitRisk"
      },
      {
        "n": "MeishiFoodGroupSubmitLogic"
      },
      {
        "n": "FoodSubmitStatic"
      }
    ],
    "logics": [
      {
        "n": "MeishiCommonDuoLifecycle1"
      },
      {
        "n": "MeishiCommonEventNav1"
      },
      {
        "n": "MeishiUtilAutoReporterInstance1"
      },
      {
        "n": "MeishiCommonEventLx1"
      }
    ],
    "nodeDataMap": {
      "MeishiCommonDuoParams": {
        "i": "757",
        "p": {
          "lxCommonParams": {
            "channelName": "meishi",
            "pageInfoKey": "group-order-submit",
            "commonParams": {
              "is_mvp": "0",
              "deal_id": "1635198936",
              "poi_id": "1851844943",
              "tab_name": 0,
              "is_distribute": 0,
              "source": "-999",
              "scene_type": "1",
              "deal_sale_count": -999,
              "deal_count": "-999",
              "distribute_deal_count": -999,
              "bundle_product_source": 0,
              "page_version": "2",
              "page_module": "0",
              "has_text": 0,
              "submit_deal_info": "-999",
              "is_person_order_same_phone_number": 0,
              "is_person_login_same_phone_number": 0,
              "is_null": 1
            },
            "cid": "c_meishi_rao5v99i"
          },
          "themeColor": {
            "mainColorValue": "#FF4B10"
          }
        },
        "pc": {
          "magicMemberPreview": {
            "r": true
          }
        }
      },
      "TopBottomSlide": {
        "i": "136",
        "p": {
          "keyboardAvoidBehavior": "padding",
          "keyboardVerticalOffset": 180,
          "moduleNodeConfigs": [
            {
              "n": "TetuanIpTips",
              "p": 1
            },
            {
              "n": "MeishiGroupBuyTab",
              "p": 1
            },
            {
              "n": "KaMopSingleTitle",
              "p": 1
            },
            {
              "n": "CartGroupDealListBg",
              "p": 2
            },
            {
              "n": "CartGroupDealList",
              "p": 2
            },
            {
              "n": "MopDataContainer",
              "p": 2
            },
            {
              "n": "MopContainer",
              "p": 1
            },
            {
              "n": "MeishiTopLinear",
              "p": 2
            },
            {
              "n": "Notice",
              "p": 2
            },
            {
              "n": "Product",
              "p": 2
            },
            {
              "n": "ProductTips",
              "p": 2
            },
            {
              "n": "GroupSubmitGiftTips",
              "p": 2
            },
            {
              "n": "TotalPrice",
              "p": 2
            },
            {
              "n": "Desk",
              "p": 2
            },
            {
              "n": "Card1",
              "p": 2
            },
            {
              "n": "Total",
              "p": 2
            },
            {
              "n": "MagicmemberPreview",
              "p": 2
            },
            {
              "n": "VipCard",
              "p": 2
            },
            {
              "n": "TieSale",
              "p": 2
            },
            {
              "n": "TieInSaleV3",
              "p": 2
            },
            {
              "n": "PayType",
              "p": 2
            },
            {
              "n": "PayFront",
              "p": 2
            },
            {
              "n": "InvitePay",
              "p": 2
            },
            {
              "n": "AfterPay",
              "p": 2
            },
            {
              "n": "Authorization",
              "p": 2
            },
            {
              "n": "BottomFill",
              "p": 2
            },
            {
              "n": "BottomBar",
              "p": 3
            }
          ],
          "sliderMaxHeight": "95%",
          "statusBarStyle": "dark-content",
          "hideKeyboardOnScroll": false,
          "safeAreaBottom": "none",
          "showSlideModal": true,
          "maskClosable": true,
          "statusBarTranslucent": true,
          "slideCloseKey": "CLOSE_POP_SLIDER_MODAL",
          "hiddenLifecycleComponent": true,
          "keyboardShouldPersistTaps": "handled",
          "slideClosePage": true,
          "disableDownClosePage": false,
          "sliderHeight": "85.0%",
          "scrollStyle": {
            "paddingLeft": 8,
            "paddingRight": 8
          },
          "loadingkey": "group-order-submit",
          "bounces": true,
          "hasMetric": true,
          "hiddenSkeleton": true
        },
        "s": {
          "slideModalStyle": {
            "borderTopRightRadius": 20,
            "borderTopLeftRadius": 20
          },
          "contentStyle": {
            "backgroundColor": "transparent"
          },
          "bottomStyle": {
            "backgroundColor": "#f7f7f7",
            "position": "relative",
            "bottom": 0,
            "zIndex": 2
          },
          "bottomSafeAreaStyle": {
            "backgroundColor": "#fff"
          },
          "topStyle": {
            "backgroundColor": "#f7f7f7",
            "position": "relative"
          }
        }
      },
      "MeishiGroupBuyTab": {
        "i": "397",
        "p": {
          "buyScene": "1",
          "pageScene": 5,
          "pureBgColor": true,
          "tabInfoList": [
            {
              "pageScene": 5,
              "tabTitle": "秒提·到店取",
              "tabTag": "3",
              "tabStyle": 0
            },
            {
              "pageScene": 1,
              "tabTitle": "买团购",
              "tabTag": "3",
              "tabStyle": 0
            }
          ],
          "multiTabScene": 1,
          "queryTabType": "5",
          "lx": {
            "channelName": "meishi",
            "pageInfoKey": "group-order-submit",
            "commonParams": {
              "is_mvp": "0",
              "deal_id": "1635198936",
              "poi_id": "1851844943",
              "tab_name": 0,
              "is_distribute": 0,
              "source": "-999",
              "scene_type": "1",
              "deal_sale_count": -999,
              "deal_count": "-999",
              "distribute_deal_count": -999,
              "bundle_product_source": 0,
              "page_version": "2",
              "page_module": "0",
              "has_text": 0,
              "submit_deal_info": "-999",
              "is_person_order_same_phone_number": 0,
              "is_person_login_same_phone_number": 0,
              "is_null": 1
            },
            "cid": "c_meishi_rao5v99i"
          }
        },
        "s": {
          "wrapStyle": {
            "marginRight": 0,
            "backgroundColor": "transparent",
            "paddingLeft": 0,
            "marginLeft": 0,
            "paddingRight": 0,
            "zIndex": 1
          }
        },
        "pc": {
          "pageScene": {
            "r": true
          },
          "multiTabScene": {
            "r": true
          },
          "cartTempProductList": {
            "r": true
          }
        },
        "e": {
          "e": {
            "defaultOnTabClick": [
              {
                "n": "MeishiGroupSubmitMrnWapper",
                "e": "onTableClick",
                "t": [
                  {
                    "t": "tabItem",
                    "f": ""
                  }
                ]
              }
            ],
            "onTabClick": [
              {
                "n": "MopContainer",
                "e": "onMiaoTiUpdate",
                "t": [
                  {
                    "t": "tabType",
                    "f": ""
                  },
                  {
                    "t": "payload.tabSelect",
                    "f": ""
                  }
                ]
              }
            ]
          }
        }
      },
      "MopContainer": {
        "i": "413",
        "p": {
          "transferData": {
            "quantity": "1"
          },
          "pageQuery": {
            "mrn_transparent": "true",
            "mrn_biz": "meishi",
            "mrn_entry": "c-group-order-submit",
            "tabType": "5",
            "nibBizConsistency": "gmV2peeKZ5C2xJqoC9o14IlfIQJKqkO42Jf4ABsGz-8KD454ZUT648SFJb5Xmlo-tSFK7mzIGLe9XMWA2Gt70lqnXoh_w-Ie4GlDqMzVbsILHK32-TwlhfYua1xXe04oGaK6dN6Wd6iqiBtzdh_feoZSXeCLumIVI8-FFsw5IPUd5gp7A-VOgaJUWSNCZwET0yUZRs0yqKhc-jKVtIaNIE4vuEIgMJur7tFe--Ua7tcBIGYNj3Rrq8B75n3Z9Zf6o1C3qmDlDxCEZzaULtTx2JQ-Q-7e_98y5sNaY7LgBx4",
            "trafficSourceActivityId": "",
            "sec_source": "rhhj_dd",
            "isOnlyShowShopCart": "false",
            "mrn_component": "GroupOrderSubmit",
            "isDealJudge": "",
            "_referer": "food-poi",
            "flexibleJSON": {
              "assignProm": []
            },
            "mrn_hideNextNavBar": "true",
            "hideLoading": "true",
            "groupBuyMopScene": "1",
            "hasKNBParams": "1",
            "venueId": "",
            "mlive_ext": "",
            "buyPoiIdEncrypt": "qB4r17707da606bc98ea64a037925971660ee8e63d7690a06106e1ce2a76ee607d88922f49ead8b8b2b7712a292610e43d2bac167cdcda7719f50f20vxu5",
            "source": "",
            "mrn_adjustParentFrame": "true",
            "productType": "",
            "dealId": "1635198936",
            "lng": "121.52897062950872",
            "halfScreenSubmitHeight": "0.85",
            "payPrice": "30.9",
            "showPrice": "30.9",
            "shelfFusion": "true",
            "lat": "31.273660438522672",
            "dd_source": "",
            "mrn_hideloading": "true",
            "govPromotion": "",
            "isTransparent": "true",
            "buyPoiId": "1851844943",
            "mrn_min_version": "2.115.0",
            "campaignId": ""
          },
          "commonParam": {
            "location": {
              "lat": "31.273660438522672",
              "lng": "121.52897062950872",
              "accuracy": "7.363734436363329"
            },
            "isSubmit": "",
            "storage": {},
            "isUpdate": "",
            "fingerprint": {
              "fingerprint": ""
            },
            "isCheck": "",
            "isPreview": "true",
            "cityInfo": {
              "cityId": "10",
              "locCityId": "10"
            },
            "systemInfo": {
              "IS_HOTEL": "",
              "mpAppVersion": "",
              "userAgent": "",
              "version": "12.56.200",
              "isWeb": "",
              "mpPluginAppId": "",
              "IS_TICKET": "",
              "isDebug": "",
              "IS_DP": "",
              "envInWeb": {},
              "platform": "ios",
              "systemVersion": "26.3.1",
              "mpAppId": "",
              "IS_MT": "true",
              "isMRN": "true",
              "isWeChatMiniProgram": "",
              "device": ""
            },
            "userInfo": {
              "uuidV2": "00000000000007A0030108A0C430C88DF8E7BA59BF348A177457840783633080",
              "userId": "3842765890",
              "mtuuid": "00000000000007A0030108A0C430C88DF8E7BA59BF348A177457840783633080",
              "unionId": "8b854f09f2814f2cb120f473ac3930eea176350111025506278",
              "uuid": "00000000000007A0030108A0C430C88DF8E7BA59BF348A177457840783633080",
              "token": "AgFsIpe7YXQee_IBR4ln-oXXq_F6jtq2AOMT_6oEuvwbZm3IQkWpq9RK7ZiTZb-EXRonInIFDWyzYAAAAAAENAAA2w_Qkp6xP7nbBz0_CIKZwutJA8YJUz3UHNqjoIPrlkhqnK4I_I3ifwXnnfUT-7KV",
              "dpid": ""
            }
          },
          "tabInfoList": [
            {
              "pageScene": 5,
              "tabTitle": "秒提·到店取",
              "tabTag": "3",
              "tabStyle": 0
            },
            {
              "pageScene": 1,
              "tabTitle": "买团购",
              "tabTag": "3",
              "tabStyle": 0
            }
          ],
          "tabHeight": 44,
          "effectiveScreenPer": "85.0%",
          "onlineOrderPropsVo": {
            "mopShopInfoVO": {
              "shopId": "1851844943",
              "shopIcon": "<https://p0.meituan.net/40.40/travelcube/7b5cf1381d1f3c7e1d0896a84dcc56c627952.jpg>",
              "shopName": "瑞幸咖啡（互联宝地二期店）",
              "shopAddress": "杨浦区黄兴路221号互联宝地二期负1层B1-68",
              "chooseShopUrl": "imeituan://www.meituan.com/mrn?mrn_biz=meishi&mrn_entry=ka-mop-poi-select&mrn_component=kaMopPoiSelect&dishSource=10&shopId=1851844943&dealId=1635198936&brandId=288&jumpToShopSelectPageOnLoad=true&pageSource=instant-order-page",
              "distance": 228,
              "distanceDesc": "228m",
              "brandId": "288",
              "topTipList": [
                {
                  "content": "附近有多家门店，请确认是否在本店取餐",
                  "type": 0
                }
              ],
              "bottomTipList": [],
              "topTipRichTextList": [
                {
                  "content": "<span style='color: #888888;'>距您228m，杨浦区黄兴路221号互联宝地二期负1层B1-68</span>",
                  "type": 0
                },
                {
                  "content": "<span style='color: #888888;'>附近有<span style='color: #FF4B10;'>多家门店</span>，请确认取餐门店</span>",
                  "type": 0
                }
              ],
              "tipList": []
            },
            "mopBrandInfoVO": {
              "brandId": "288",
              "mopBrandType": 20
            },
            "mopDealMappingInfoVO": {
              "mopDealMappingProductInfoVO": {
                "dealId": 1635198936,
                "dealIdStr": "1635198936",
                "dealTag": 1,
                "dealName": "【限量周边】联名光栅卡挂件双杯套餐",
                "mappingId": "2864067541",
                "dealMappingType": 30,
                "mopComboDishDataVO": {
                  "comboProductId": "2312258382",
                  "comboSkuId": "2864067541",
                  "productType": 40,
                  "comboName": "【限量周边】联名光栅卡挂件双杯套餐",
                  "minPrice": "5200",
                  "directAdd": false,
                  "media": {
                    "type": 60,
                    "image": "<https://img.meituan.net/shopdirectconnectpic/abbbfba1279b01072e99fbb49537d64b.jpg>",
                    "backgroundImage": "<http://p0.meituan.net/biztone/eebace0e4375a157dfbf6d285d04e56c4671.png@252w_252h_1e_1c>",
                    "imageList": [
                      "<https://img.meituan.net/shopdirectconnectpic/582a75d2de7f0b9bfc5a7d54725f4a2a.jpg>"
                    ]
                  },
                  "soldOut": false,
                  "stockStatus": 2,
                  "stock": -1,
                  "comboDishGroupList": [
                    {
                      "comboGroupName": "饮品",
                      "comboGroupId": "饮品-0",
                      "comboDishItemList": [
                        {
                          "spuId": "840935279",
                          "spuName": "生椰拿铁",
                          "skuIdList": [
                            "2873171508",
                            "2873171507",
                            "2873171509"
                          ],
                          "rank": 1,
                          "media": {
                            "type": 20,
                            "image": "<https://img.meituan.net/shopdirectconnectpic/3575dbfa0a59899724b5d906954873e7.jpg>",
                            "backgroundImage": "<http://p0.meituan.net/biztone/eebace0e4375a157dfbf6d285d04e56c4671.png@252w_252h_1e_1c>",
                            "imageList": [
                              "<https://img.meituan.net/shopdirectconnectpic/bf2e8038eb58a9796134ed2a21070709.jpg>"
                            ]
                          },
                          "soldOut": false,
                          "stockStatus": 2,
                          "spuStock": -1,
                          "currentPrice": "0",
                          "canCustomization": true,
                          "defaultChooseNum": 0,
                          "defaultChooseSku": {
                            "skuId": "2873171508",
                            "premiumList": [
                              {
                                "premiumId": "2540459141",
                                "selectNum": 1
                              },
                              {
                                "premiumId": "2540423644",
                                "selectNum": 1
                              },
                              {
                                "premiumId": "2540353556",
                                "selectNum": 1
                              },
                              {
                                "premiumId": "2540340500",
                                "selectNum": 1
                              }
                            ]
                          },
                          "needQi": true
                        },
                        {
                          "spuId": "2229378235",
                          "spuName": "小黄油拿铁",
                          "skuIdList": [
                            "2873141811",
                            "2873141813",
                            "2873141812"
                          ],
                          "rank": 2,
                          "media": {
                            "type": 20,
                            "image": "<https://img.meituan.net/shopdirectconnectpic/260e5f3d8a4a89e9869cbd8d9527d63f.jpg>",
                            "backgroundImage": "<http://p0.meituan.net/biztone/eebace0e4375a157dfbf6d285d04e56c4671.png@252w_252h_1e_1c>",
                            "imageList": [
                              "<https://img.meituan.net/shopdirectconnectpic/7a7ae382aa8ccb310ac3c520ab8c0770.jpg>"
                            ]
                          },
                          "soldOut": false,
                          "stockStatus": 2,
                          "spuStock": -1,
                          "currentPrice": "0",
                          "canCustomization": true,
                          "defaultChooseNum": 0,
                          "defaultChooseSku": {
                            "skuId": "2873141811",
                            "premiumList": [
                              {
                                "premiumId": "2540444295",
                                "selectNum": 1
                              },
                              {
                                "premiumId": "2540330704",
                                "selectNum": 1
                              },
                              {
                                "premiumId": "2540301874",
                                "selectNum": 1
                              },
                              {
                                "premiumId": "2540280964",
                                "selectNum": 1
                              }
                            ]
                          },
                          "needQi": true
                        },
                        {
                          "spuId": "2290264283",
                          "spuName": "苦瓜轻体果蔬茶",
                          "skuIdList": [
                            "2878647420",
                            "2878647421"
                          ],
                          "rank": 3,
                          "media": {
                            "type": 20,
                            "image": "<https://img.meituan.net/shopdirectconnectpic/1f1bc1a6bf89a59067b0d6b8928d33fa.jpg>",
                            "backgroundImage": "<http://p0.meituan.net/biztone/eebace0e4375a157dfbf6d285d04e56c4671.png@252w_252h_1e_1c>",
                            "imageList": [
                              "<https://img.meituan.net/shopdirectconnectpic/8e3a8ae3186bcd9d1454795ac047de81.jpg>"
                            ]
                          },
                          "soldOut": false,
                          "stockStatus": 2,
                          "spuStock": -1,
                          "currentPrice": "0",
                          "canCustomization": true,
                          "defaultChooseNum": 0,
                          "defaultChooseSku": {
                            "skuId": "2878647420",
                            "premiumList": [
                              {
                                "premiumId": "2559186640",
                                "selectNum": 1
                              },
                              {
                                "premiumId": "2566595052",
                                "selectNum": 1
                              },
                              {
                                "premiumId": "2559269700",
                                "selectNum": 1
                              }
                            ]
                          },
                          "needQi": false
                        },
                        {
                          "spuId": "2304702978",
                          "spuName": "冰吸生椰拿铁（首创）",
                          "skuIdList": [
                            "2878676656",
                            "2878676655"
                          ],
                          "rank": 4,
                          "media": {
                            "type": 20,
                            "image": "<https://img.meituan.net/shopdirectconnectpic/58a3183d01da56707b3652d362209189.jpg>",
                            "backgroundImage": "<http://p0.meituan.net/biztone/eebace0e4375a157dfbf6d285d04e56c4671.png@252w_252h_1e_1c>",
                            "imageList": [
                              "<https://img.meituan.net/shopdirectconnectpic/a99caf2fe40a179324b603b2ad14c607.jpg>"
                            ]
                          },
                          "soldOut": false,
                          "stockStatus": 2,
                          "spuStock": -1,
                          "currentPrice": "0",
                          "canCustomization": true,
                          "defaultChooseNum": 0,
                          "defaultChooseSku": {
                            "skuId": "2878676656",
                            "premiumList": [
                              {
                                "premiumId": "2559347768",
                                "selectNum": 1
                              },
                              {
                                "premiumId": "2559404566",
                                "selectNum": 1
                              },
                              {
                                "premiumId": "2559402655",
                                "selectNum": 1
                              },
                              {
                                "premiumId": "2559351882",
                                "selectNum": 1
                              }
                            ]
                          },
                          "needQi": true
                        },
                        {
                          "spuId": "2316930928",
                          "spuName": "陨石拿铁",
                          "skuIdList": [
                            "2878658750",
                            "2878658749"
                          ],
                          "rank": 5,
                          "media": {
                            "type": 20,
                            "image": "<https://img.meituan.net/shopdirectconnectpic/c619515c3563ee05a7ae72138b28ba62.jpg>",
                            "backgroundImage": "<http://p0.meituan.net/biztone/eebace0e4375a157dfbf6d285d04e56c4671.png@252w_252h_1e_1c>",
                            "imageList": [
                              "<https://img.meituan.net/shopdirectconnectpic/256630f40ae771533364d5dbfce38fa4.jpg>"
                            ]
                          },
                          "soldOut": false,
                          "stockStatus": 2,
                          "spuStock": -1,
                          "currentPrice": "0",
                          "canCustomization": true,
                          "defaultChooseNum": 0,
                          "defaultChooseSku": {
                            "skuId": "2878658750",
                            "premiumList": [
                              {
                                "premiumId": "2559210984",
                                "selectNum": 1
                              },
                              {
                                "premiumId": "2559242608",
                                "selectNum": 1
                              },
                              {
                                "premiumId": "2559333065",
                                "selectNum": 1
                              },
                              {
                                "premiumId": "2559376102",
                                "selectNum": 1
                              }
                            ]
                          },
                          "needQi": true
                        },
                        {
                          "spuId": "2317735733",
                          "spuName": "轻咖 柠檬茶（超大杯）",
                          "skuIdList": [
                            "2880849817"
                          ],
                          "rank": 6,
                          "media": {
                            "type": 20,
                            "image": "<https://img.meituan.net/shopdirectconnectpic/ee58ca72a73321f7cdfeeac0cc74b10b.jpg>",
                            "backgroundImage": "<http://p0.meituan.net/biztone/eebace0e4375a157dfbf6d285d04e56c4671.png@252w_252h_1e_1c>",
                            "imageList": [
                              "<https://img.meituan.net/shopdirectconnectpic/700536dfbd626c87485aabd497507030.jpg>"
                            ]
                          },
                          "soldOut": false,
                          "stockStatus": 2,
                          "spuStock": -1,
                          "currentPrice": "0",
                          "canCustomization": true,
                          "defaultChooseNum": 0,
                          "defaultChooseSku": {
                            "skuId": "2880849817",
                            "premiumList": [
                              {
                                "premiumId": "2565180779",
                                "selectNum": 1
                              },
                              {
                                "premiumId": "2565322176",
                                "selectNum": 1
                              },
                              {
                                "premiumId": "2565364149",
                                "selectNum": 1
                              },
                              {
                                "premiumId": "2565266242",
                                "selectNum": 1
                              }
                            ]
                          },
                          "needQi": false
                        },
                        {
                          "spuId": "841630645",
                          "spuName": "橙C美式",
                          "skuIdList": [
                            "2873155689",
                            "2873155688"
                          ],
                          "rank": 7,
                          "media": {
                            "type": 20,
                            "image": "<https://img.meituan.net/shopdirectconnectpic/853f61fcf4ceeee4da067ad73fdc5ef7.jpg>",
                            "backgroundImage": "<http://p0.meituan.net/biztone/eebace0e4375a157dfbf6d285d04e56c4671.png@252w_252h_1e_1c>",
                            "imageList": [
                              "<https://img.meituan.net/shopdirectconnectpic/0a656446e8100cbe0d183dd486ea9a8e.jpg>"
                            ]
                          },
                          "soldOut": false,
                          "stockStatus": 2,
                          "spuStock": -1,
                          "currentPrice": "0",
                          "canCustomization": true,
                          "defaultChooseNum": 0,
                          "defaultChooseSku": {
                            "skuId": "2873155689",
                            "premiumList": [
                              {
                                "premiumId": "2540410001",
                                "selectNum": 1
                              },
                              {
                                "premiumId": "2540338659",
                                "selectNum": 1
                              },
                              {
                                "premiumId": "2540338660",
                                "selectNum": 1
                              },
                              {
                                "premiumId": "2540397275",
                                "selectNum": 1
                              },
                              {
                                "premiumId": "2540353638",
                                "selectNum": 1
                              }
                            ]
                          },
                          "needQi": true
                        }
                      ],
                      "rank": 0,
                      "fixed": false,
                      "minChoiceNum": 2,
                      "maxChoiceNum": 2,
                      "repeatChooseNum": 2,
                      "showPrice": true
                    },
                    {
                      "comboGroupName": "周边",
                      "comboGroupId": "周边-1",
                      "comboDishItemList": [
                        {
                          "spuId": "2317597872",
                          "spuName": "光栅卡挂件·自嘲熊和朋友们系列",
                          "skuIdList": [
                            "2880906263"
                          ],
                          "rank": 1,
                          "media": {
                            "type": 20,
                            "image": "<https://img.meituan.net/shopdirectconnectpic/fd46d472ca2919616311af2fe0be12ea.jpg>",
                            "backgroundImage": "<http://p0.meituan.net/biztone/eebace0e4375a157dfbf6d285d04e56c4671.png@252w_252h_1e_1c>",
                            "imageList": [
                              "<https://img.meituan.net/shopdirectconnectpic/44fe3a42b4ce7511a046b52f1d992a06.jpg>"
                            ]
                          },
                          "soldOut": false,
                          "stockStatus": 1,
                          "spuStock": 5,
                          "currentPrice": "0",
                          "canCustomization": false,
                          "defaultChooseNum": 0,
                          "defaultChooseSku": {
                            "skuId": "2880906263",
                            "premiumList": []
                          },
                          "needQi": false
                        }
                      ],
                      "rank": 1,
                      "fixed": false,
                      "minChoiceNum": 1,
                      "maxChoiceNum": 1,
                      "repeatChooseNum": 1,
                      "showPrice": true
                    }
                  ],
                  "extendInfoMap": {
                    "COMBO_ADD_PRICE_WITH_RAW": "1"
                  },
                  "needQi": false
                }
              },
              "isSupport": true,
              "dealUpperLimit": 100,
              "skuUpperLimit": 15
            },
            "mopProductPriceVO": {
              "currentPrice": "3090",
              "mopCurrentPrice": "null",
              "dealCurrentPrice": "3090",
              "discountPrice": "4510",
              "totalPrice": "7600",
              "selectNum": 1,
              "dealTotalPrice": "7600",
              "dealDiscountPrice": "4510",
              "needQi": false
            },
            "currentPage": 10,
            "usePromotionDetails": [
              {
                "promoId": "685890111740298235",
                "promoType": 6,
                "totalDiscount": 300,
                "activityProductId": 11,
                "title": "神券-吃喝玩乐神券"
              }
            ]
          }
        },
        "s": {
          "wrapCardStyle": {
            "position": "relative",
            "zIndex": 1
          }
        },
        "pc": {
          "mopTempCartTempProductList": {
            "r": true
          }
        },
        "e": {
          "e": {
            "onSubmitSuccess": [
              {
                "n": "BottomBar",
                "e": "onSubmitSuccess",
                "t": [
                  {
                    "t": "",
                    "f": ""
                  }
                ]
              }
            ]
          }
        }
      },
      "MopDataContainer": {
        "i": "430",
        "p": {
          "quantity": "1"
        },
        "s": {
          "wrapStyle": {
            "marginRight": 0,
            "marginLeft": 0
          }
        },
        "pc": {
          "quantity": {
            "r": true
          },
          "mopTempData": {
            "r": true
          }
        }
      },
      "AfterPay": {
        "i": "132",
        "t": "l",
        "p": {
          "afterPayList": [],
          "tailTips": [],
          "lx": {
            "channelName": "meishi",
            "pageInfoKey": "group-order-submit",
            "commonParams": {
              "is_mvp": "0",
              "deal_id": "1635198936",
              "poi_id": "1851844943",
              "tab_name": 0,
              "is_distribute": 0,
              "source": "-999",
              "scene_type": "1",
              "deal_sale_count": -999,
              "deal_count": "-999",
              "distribute_deal_count": -999,
              "bundle_product_source": 0,
              "page_version": "2",
              "page_module": "0",
              "has_text": 0,
              "submit_deal_info": "-999",
              "is_person_order_same_phone_number": 0,
              "is_person_login_same_phone_number": 0,
              "is_null": 1
            },
            "cid": "c_meishi_rao5v99i",
            "insurance_mc": {
              "bid": "b_meishi_h0kdj3z1_mc",
              "valLab": {
                "poi_id": "-999"
              }
            },
            "insurance_mv": {
              "bid": "b_meishi_h0kdj3z1_mv",
              "valLab": {
                "poi_id": "-999"
              }
            },
            "full_rebate_mv": {
              "bid": "b_meishi_hk57o0vx_mv",
              "valLab": {
                "activity_id": [],
                "page_version": "2"
              }
            },
            "full_rebate_mc": {
              "bid": "b_meishi_hk57o0vx_mc",
              "valLab": {
                "activity_id": [],
                "page_version": "2"
              }
            },
            "coupon_return_mv": {
              "bid": "b_meishi_vfisf00l_mv"
            }
          },
          "isTetuan": false
        },
        "s": {
          "cardWrapStyle": {
            "marginBottom": 0
          }
        },
        "pc": {
          "afterPayList": {
            "r": true
          }
        }
      },
      "BottomFill": {
        "i": "509",
        "t": "l",
        "p": {
          "full": false
        }
      },
      "DzBgLineargradient": {
        "i": "239",
        "t": "l",
        "p": {
          "start": {
            "x": 0,
            "y": 0
          },
          "end": {
            "x": 0,
            "y": 1
          },
          "colors": [
            "#FFFFFF",
            "#F4F4F4"
          ]
        },
        "s": {
          "wrapCardStyle": {
            "top": 43,
            "left": 0,
            "bottom": 0,
            "position": "absolute",
            "right": 0,
            "height": 150,
            "zIndex": 0
          }
        }
      },
      "MaxLeezCard": {
        "i": "37",
        "s": {
          "style": {
            "padding": 0,
            "margin": 0,
            "backgroundColor": "#f7f7f7",
            "paddingBottom": 0,
            "top": 0,
            "left": 0,
            "bottom": 0,
            "paddingRight": 0,
            "paddingTop": 0,
            "position": "absolute",
            "right": 0,
            "paddingLeft": 0
          }
        }
      },
      "MaxLeezCard1": {
        "i": "37",
        "s": {
          "style": {
            "padding": 0,
            "backgroundColor": "#ffffff",
            "right": 0,
            "borderRadius": 0,
            "left": 0,
            "height": 100
          }
        }
      },
      "DzBgLineargradient2": {
        "i": "239",
        "t": "l",
        "p": {
          "start": {
            "x": 0,
            "y": 0
          },
          "end": {
            "x": 0,
            "y": 1
          },
          "colors": [
            "#FFFFFF",
            "#F4F4F4"
          ]
        },
        "s": {
          "wrapCardStyle": {
            "position": "relative",
            "right": 0,
            "left": 0,
            "height": 100
          }
        }
      },
      "TopTag": {
        "i": "155",
        "t": "l",
        "p": {
          "labelList": [],
          "closeEmitKey": "CLOSE_POP_SLIDER_MODAL",
          "lx": {
            "channelName": "meishi",
            "pageInfoKey": "group-order-submit",
            "commonParams": {
              "is_mvp": "0",
              "deal_id": "1635198936",
              "poi_id": "1851844943",
              "tab_name": 0,
              "is_distribute": 0,
              "source": "-999",
              "scene_type": "1",
              "deal_sale_count": -999,
              "deal_count": "-999",
              "distribute_deal_count": -999,
              "bundle_product_source": 0,
              "page_version": "2",
              "page_module": "0",
              "has_text": 0,
              "submit_deal_info": "-999",
              "is_person_order_same_phone_number": 0,
              "is_person_login_same_phone_number": 0,
              "is_null": 1
            },
            "cid": "c_meishi_rao5v99i",
            "closeMc": {
              "bid": "b_meishi_byrm830y_mc"
            },
            "valLab": {
              "status": 0,
              "tab_name": "秒提·到店取",
              "deal_id": "1635198936",
              "poi_id": "1851844943",
              "mode_type": 2
            }
          },
          "labels": [],
          "closeVisible": true,
          "full": false
        },
        "s": {
          "wrapCardStyle": {
            "marginBottom": 13
          }
        }
      },
      "Dialog": {
        "i": "142",
        "t": "l",
        "p": {
          "reportTags": {
            "errCode": 0,
            "errMsg": "成功",
            "errUserMsg": "成功",
            "dpWX": false,
            "mtWX": false,
            "source": "food-poi",
            "routeByPortm": "0"
          },
          "isFoodPopBack": true,
          "lx": {
            "channelName": "meishi",
            "pageInfoKey": "group-order-submit",
            "commonParams": {
              "is_mvp": "0",
              "deal_id": "1635198936",
              "poi_id": "1851844943",
              "tab_name": 0,
              "is_distribute": 0,
              "source": "-999",
              "scene_type": "1",
              "deal_sale_count": -999,
              "deal_count": "-999",
              "distribute_deal_count": -999,
              "bundle_product_source": 0,
              "page_version": "2",
              "page_module": "0",
              "has_text": 0,
              "submit_deal_info": "-999",
              "is_person_order_same_phone_number": 0,
              "is_person_login_same_phone_number": 0,
              "is_null": 1
            },
            "cid": "c_meishi_rao5v99i",
            "module_mv": {
              "bid": "b_meishi_lvzq6i2d_mv"
            },
            "confirm_mc": {
              "bid": "b_meishi_zv9z65nj_mc"
            },
            "valLab": {
              "card_id": "",
              "title": "成功"
            }
          },
          "reportMsg": "",
          "scene": "food-order-submit-add"
        },
        "e": {
          "e": {
            "onReload": [
              {
                "n": "MeishiCommonDuoLifecycle1",
                "e": "update"
              }
            ]
          }
        }
      },
      "MeishiKaMopDuoSubmitRemindModal": {
        "i": "642",
        "p": {},
        "e": {
          "e": {
            "onReload": [
              {
                "n": "MeishiCommonDuoLifecycle1",
                "e": "update"
              }
            ]
          }
        }
      },
      "MeishiKaMopCheckShopModal": {
        "i": "403",
        "p": {
          "buyScene": "1",
          "pageQuery": {
            "mrn_transparent": "true",
            "mrn_biz": "meishi",
            "mrn_entry": "c-group-order-submit",
            "tabType": "5",
            "nibBizConsistency": "gmV2peeKZ5C2xJqoC9o14IlfIQJKqkO42Jf4ABsGz-8KD454ZUT648SFJb5Xmlo-tSFK7mzIGLe9XMWA2Gt70lqnXoh_w-Ie4GlDqMzVbsILHK32-TwlhfYua1xXe04oGaK6dN6Wd6iqiBtzdh_feoZSXeCLumIVI8-FFsw5IPUd5gp7A-VOgaJUWSNCZwET0yUZRs0yqKhc-jKVtIaNIE4vuEIgMJur7tFe--Ua7tcBIGYNj3Rrq8B75n3Z9Zf6o1C3qmDlDxCEZzaULtTx2JQ-Q-7e_98y5sNaY7LgBx4",
            "trafficSourceActivityId": "",
            "sec_source": "rhhj_dd",
            "isOnlyShowShopCart": "false",
            "mrn_component": "GroupOrderSubmit",
            "isDealJudge": "",
            "_referer": "food-poi",
            "flexibleJSON": {
              "assignProm": []
            },
            "mrn_hideNextNavBar": "true",
            "hideLoading": "true",
            "groupBuyMopScene": "1",
            "hasKNBParams": "1",
            "venueId": "",
            "mlive_ext": "",
            "buyPoiIdEncrypt": "qB4r17707da606bc98ea64a037925971660ee8e63d7690a06106e1ce2a76ee607d88922f49ead8b8b2b7712a292610e43d2bac167cdcda7719f50f20vxu5",
            "source": "",
            "mrn_adjustParentFrame": "true",
            "productType": "",
            "dealId": "1635198936",
            "lng": "121.52897062950872",
            "halfScreenSubmitHeight": "0.85",
            "payPrice": "30.9",
            "showPrice": "30.9",
            "shelfFusion": "true",
            "lat": "31.273660438522672",
            "dd_source": "",
            "mrn_hideloading": "true",
            "govPromotion": "",
            "isTransparent": "true",
            "buyPoiId": "1851844943",
            "mrn_min_version": "2.115.0",
            "campaignId": ""
          },
          "chooseShopUrl": "imeituan://www.meituan.com/mrn?mrn_biz=meishi&mrn_entry=ka-mop-poi-select&mrn_component=kaMopPoiSelect&dishSource=10&shopId=1851844943&dealId=1635198936&brandId=288&jumpToShopSelectPageOnLoad=true&pageSource=instant-order-page",
          "disableSwitchShop": false,
          "location": {
            "lat": "31.273660438522672",
            "lng": "121.52897062950872",
            "accuracy": "7.363734436363329"
          },
          "isFromTetuan": false
        },
        "e": {
          "e": {
            "onSwitchShop": [
              {
                "n": "MeishiCommonDuoLifecycle1",
                "e": "update"
              }
            ],
            "onConfirmOrder": [
              {
                "n": "BottomBar",
                "e": "onMiaoTiSubmitPress",
                "t": [
                  {
                    "t": "miaoTiConfirm",
                    "f": ""
                  }
                ]
              }
            ]
          }
        }
      },
      "SubmitRisk": {
        "i": "192",
        "p": {
          "yodaEnv": "Prod",
          "lx": [],
          "yodaRequestParams": {
            "os": "ios",
            "platform": "mt",
            "version": "12.56.200",
            "uuid": "00000000000007A0030108A0C430C88DF8E7BA59BF348A177457840783633080",
            "userId": "3842765890",
            "token": "AgFsIpe7YXQee_IBR4ln-oXXq_F6jtq2AOMT_6oEuvwbZm3IQkWpq9RK7ZiTZb-EXRonInIFDWyzYAAAAAAENAAA2w_Qkp6xP7nbBz0_CIKZwutJA8YJUz3UHNqjoIPrlkhqnK4I_I3ifwXnnfUT-7KV"
          }
        },
        "e": {
          "e": {
            "onSurePress": [
              {
                "n": "BottomBar",
                "e": "onSubmitPress",
                "t": [
                  {
                    "t": "sType",
                    "f": ""
                  }
                ]
              }
            ]
          }
        }
      },
      "MeishiFoodGroupSubmitLogic": {
        "i": "248",
        "p": {
          "dealId": "1635198936",
          "CID": "c_meishi_rao5v99i"
        }
      },
      "FoodSubmitStatic": {
        "i": "1090"
      },
      "MeishiCommonDuoLifecycle1": {
        "i": "13",
        "e": {
          "e": {
            "preview.onEngineFail": [
              {
                "n": "FoodSubmitStatic",
                "e": "onPreviewEngineFail"
              }
            ],
            "preview.onResponse": [
              {
                "n": "FoodSubmitStatic",
                "e": "onPreviewResponse"
              }
            ],
            "submit.onFail": [
              {
                "n": "SubmitRisk",
                "e": "onRiskDialogShow",
                "t": [
                  {
                    "t": "item",
                    "f": "item"
                  }
                ]
              }
            ],
            "preview.onSuccess": [
              {
                "n": "MeishiCommonEventNav1",
                "e": "setWebDocumentTitle",
                "p": {
                  "title": "提交订单"
                }
              }
            ]
          }
        }
      },
      "MeishiCommonEventNav1": {
        "i": "90"
      },
      "MeishiUtilAutoReporterInstance1": {
        "i": "91"
      },
      "MeishiCommonEventLx1": {
        "i": "16"
      }
    },
    "currentData": {
      "poiName": "瑞幸咖啡（互联宝地二期店）"
    },
    "minifyHttpResponse": 1
  },
  "bizReq": {
    "bizCode": "nib.food.groupbuy",
    "environmentParam": {
      "duoCommonParam": {
        "location": {
          "lat": "31.273660438522672",
          "lng": "121.52897062950872",
          "accuracy": "7.363734436363329"
        },
        "userInfo": {
          "userId": "3842765890",
          "token": "AgFsIpe7YXQee_IBR4ln-oXXq_F6jtq2AOMT_6oEuvwbZm3IQkWpq9RK7ZiTZb-EXRonInIFDWyzYAAAAAAENAAA2w_Qkp6xP7nbBz0_CIKZwutJA8YJUz3UHNqjoIPrlkhqnK4I_I3ifwXnnfUT-7KV",
          "uuid": "00000000000007A0030108A0C430C88DF8E7BA59BF348A177457840783633080",
          "uuidV2": "00000000000007A0030108A0C430C88DF8E7BA59BF348A177457840783633080",
          "mtuuid": "00000000000007A0030108A0C430C88DF8E7BA59BF348A177457840783633080",
          "userAgent": "com.meituan.imeituan-beta/318515 (unknown, iOS 26.3.1, iPhone, Scale/3.000000)",
          "userIp": "203.76.219.194",
          "userIpV2": "103.202.147.196",
          "unionId": "8b854f09f2814f2cb120f473ac3930eea176350111025506278",
          "dpid": "",
          "regionId": "1000330700"
        },
        "cityInfo": {
          "cityId": "10",
          "locCityId": "10"
        },
        "systemInfo": {
          "version": "12.56.200",
          "systemVersion": "26.3.1",
          "device": "",
          "platform": "ios",
          "isWeb": false,
          "isWeChatMiniProgram": false,
          "isDebug": false,
          "isMRN": true,
          "mpAppId": "",
          "envInWeb": {},
          "utmInfo": {
            "source": "Alpha",
            "medium": "iphone",
            "term": "12.56.200",
            "content": "00000000000007A0030108A0C430C88DF8E7BA59BF348A177457840783633080",
            "campaign": "AgroupBgroupD200Ghomepage_searchH0"
          },
          "mpAppVersion": "",
          "mpPluginAppId": "",
          "mtgsig": {
            "a0": "3.0",
            "a1": "bb459669-615c-4dcd-a201-8dc32aa1b5e4",
            "a3": 25,
            "a4": 1777023433,
            "a5": "JFrKR7NRpCZLqCDcdErwsoOLQFB1v6t7qXU+pQo61Idf4fnUzOgC+ijc6E+YEBdhJetir6m/np4xNV91YQ3xhTslU7nwIIvEE5LriGPupHHb3vlMEqZ9XN/pDx+WZjxgnyjt6iK2h9kaw0EPv2R1bsGMc1lTEpUKTQ4F4NqQ3FjTzVxBnr/wfmwkD7+PtwTZfJVumyumt9LOV6ExL8rhMhE6ZC8U/rTFQeEV+9zE3Rspe6sEQO7NgVPKoUcV+Fa9E5PKF4FJLofheXgTNWiVqdmvYR3HtmcQcjwpjT45BwhdiL1+0ilNWOfJvq3Epa6vWw8iVoirb602pkoJcfTZBR7WRX5YVsbBMgCytUIQhbzak8HvgFvY065CucVKzHyuHCgsO4BE8jwXRNyA",
            "a6": 0,
            "a7": "Nd4AWv4k0Fx0fpkpQ5vyLWJvwRn2izg1Ny1qe09UlJFKrLcc2tsxUqx4d3eG57Xkb2m7z+hX/hdHVooBtZn3Gbl/hBI/W/v7d+hpgBVFl7M=",
            "a8": "5395074119b4b9a92eaca0858e8c71ddf177f128cf6ee8e411d4f76a",
            "a9": "997c6780LeDBjYl3Ay12LC6GAxYVI+FNEA5cWbuwIEinWXpoTFxQ5kv13p+lIDFRc1BGMrPtNnbVqrhK0u7PAQU1EwtftNHkPqlZQymy0NqumRtOAqA0WrR5HAJVz1uRYoY6tP2ewA/pnCBrmDuMKs15H4xuC0fBxKvyJlcXtK4tTgztKa7C7IX1fy131b/0c1afIzsbdUJ2FFHV6i8Qmo5ttoJXSOToa7NAapXOpEhXIJB+bZnUALjFZfZYz0zDQH1H2WJJKdOcmzQ5AJOVGtwkhbsejRcMgBebZbGiPC/4+a7NSm0KVakplgEh+MlRAasiQ6i9qdaoG0uESyODoBTlaEvH6dMunSrbelbo6saAS21S/RiWYeDAD4Ii0FkT9/LCuHgDEiB263ffCt+RJtgh1TT6JKubzV7ju8/pmArNevpWCgI8ZCG1gA+FWh8/46ZqEp2GIY+yX/F0ER0HL6SctLuuTGLfOQciHU+cHQzr5uR8IvaCIHOA+ddYMDyAXGtQw8kkv1JAcDfH/hsFNzFJvjKKrXYiEhEj8KsaJG/J9ow3YtE35VTWGCWXz21Qt6tR72Pu4deusx2sCqTVLCjPIn0PYKhhThrju8PSrlI9Tmrp6GNpsU7y1JMvxu2fiiNdHlB9dHsjk05HTC4IV0o4dca+Od0fjf4gpOzsKak7yLSmNB0=",
            "a10": "5,202,1.1.6",
            "x0": 2,
            "a2": "6732818db69cbbd79b3e1d17c3a4aa68"
          },
          "is_HOTEL": false,
          "is_DP": false,
          "is_MT": true
        },
        "fingerprint": {
          "fingerprint": ""
        },
        "storage": {}
      },
      "submitVersion": "12.31.000",
      "pageId": 0,
      "gpsCoordinateType": "GCJ02",
      "magicMemberComponentVersion": "0.3.0"
    },
    "productParam": {
      "productId": "1635198936",
      "quantity": 1
    },
    "poiParam": {
      "poiId": "1851844943"
    },
    "merchantMemberParam": {
      "forcePut": 1
    },
    "payParam": {
      "payType": 0,
      "cashierEnvParam": {}
    },
    "promoParam": {
      "operatorPromoType": "0",
      "queryPromoLimitType": 0
    },
    "riskParam": {
      "erasePromotionType": 0,
      "yodaInfo": {}
    },
    "pageUrl": {
      "mrn_transparent": "true",
      "mrn_biz": "meishi",
      "mrn_entry": "c-group-order-submit",
      "tabType": "5",
      "nibBizConsistency": "gmV2peeKZ5C2xJqoC9o14IlfIQJKqkO42Jf4ABsGz-8KD454ZUT648SFJb5Xmlo-tSFK7mzIGLe9XMWA2Gt70lqnXoh_w-Ie4GlDqMzVbsILHK32-TwlhfYua1xXe04oGaK6dN6Wd6iqiBtzdh_feoZSXeCLumIVI8-FFsw5IPUd5gp7A-VOgaJUWSNCZwET0yUZRs0yqKhc-jKVtIaNIE4vuEIgMJur7tFe--Ua7tcBIGYNj3Rrq8B75n3Z9Zf6o1C3qmDlDxCEZzaULtTx2JQ-Q-7e_98y5sNaY7LgBx4",
      "trafficSourceActivityId": "",
      "sec_source": "rhhj_dd",
      "isOnlyShowShopCart": "false",
      "mrn_component": "GroupOrderSubmit",
      "isDealJudge": "",
      "_referer": "food-poi",
      "flexibleJSON": {
        "assignProm": []
      },
      "mrn_hideNextNavBar": "true",
      "hideLoading": "true",
      "groupBuyMopScene": "1",
      "hasKNBParams": "1",
      "venueId": "",
      "mlive_ext": "",
      "buyPoiIdEncrypt": "qB4r17707da606bc98ea64a037925971660ee8e63d7690a06106e1ce2a76ee607d88922f49ead8b8b2b7712a292610e43d2bac167cdcda7719f50f20vxu5",
      "source": "",
      "mrn_adjustParentFrame": "true",
      "productType": "",
      "dealId": "1635198936",
      "lng": "121.52897062950872",
      "halfScreenSubmitHeight": "0.85",
      "payPrice": "30.9",
      "showPrice": "30.9",
      "shelfFusion": "true",
      "lat": "31.273660438522672",
      "dd_source": "",
      "mrn_hideloading": "true",
      "govPromotion": "",
      "isTransparent": "true",
      "buyPoiId": "1851844943",
      "mrn_min_version": "2.115.0",
      "campaignId": ""
    },
    "bizExtend": {},
    "userAgreementParam": {
      "agreementInfoList": []
    },
    "pageSceneParam": {
      "pageScene": 0,
      "nextPageScene": 0,
      "promotionPosition": "2109",
      "inflatePosition": "2140",
      "pageTraceInfo": [
        "2026-04-24 17:37:13 doBizPreview   -   8893362691017239693"
      ],
      "submitBtnStatus": 0,
      "openSelectCouponPageFlag": false,
      "giftIntention": 0,
      "pageSourceId": 0
    },
    "createPriceParam": {},
    "transferDataParam": {
      "transferData": {
        "quantity": "1"
      }
    },
    "operateTypeParam": {
      "operateType": 0
    },
    "cartParam": {
      "promoParamMap": {}
    },
    "diff": false
  },
  "bizRes": {
    "code": 0,
    "message": "成功",
    "userMessage": "成功",
    "data": {
      "abTestVOList": [
        {
          "key": "ab_group_QDJBH",
          "douHuTestConfigVOList": [],
          "horizonTestConfigVOList": [
            {
              "expKey": "ab_group_QDJBH",
              "expResult": true
            }
          ],
          "arenaTestConfigVOList": []
        }
      ],
      "bizResultCode": 0,
      "pageSceneParamVO": {
        "pageScene": 5,
        "nextPageScene": 0,
        "promotionPosition": "2109",
        "pageTraceInfo": [
          "2026-04-24 17:37:13 doBizPreview   -   8893362691017239693"
        ],
        "tabInfoVO": [
          {
            "pageScene": 5,
            "tabTitle": "秒提·到店取",
            "tabTag": "3",
            "tabStyle": 0
          },
          {
            "pageScene": 1,
            "tabTitle": "买团购",
            "tabTag": "3",
            "tabStyle": 0
          }
        ],
        "submitBtnStatus": 0,
        "multiTabScene": 1,
        "switchTabType": 1,
        "backPrePageType": 1,
        "openSelectCouponPageFlag": false,
        "giftIntention": 0,
        "pageSourceId": 0
      },
      "preOrderExtParams": "",
      "afterPayInfoVO": {
        "afterPayList": []
      },
      "mopPreOrderVO": {
        "mopShopInfoVO": {
          "shopId": "1851844943",
          "shopIcon": "<https://p0.meituan.net/40.40/travelcube/7b5cf1381d1f3c7e1d0896a84dcc56c627952.jpg>",
          "shopName": "瑞幸咖啡（互联宝地二期店）",
          "shopAddress": "杨浦区黄兴路221号互联宝地二期负1层B1-68",
          "chooseShopUrl": "imeituan://www.meituan.com/mrn?mrn_biz=meishi&mrn_entry=ka-mop-poi-select&mrn_component=kaMopPoiSelect&dishSource=10&shopId=1851844943&dealId=1635198936&brandId=288&jumpToShopSelectPageOnLoad=true&pageSource=instant-order-page",
          "distance": 228,
          "distanceDesc": "228m",
          "brandId": "288",
          "topTipList": [
            {
              "content": "附近有多家门店，请确认是否在本店取餐",
              "type": 0
            }
          ],
          "bottomTipList": [],
          "topTipRichTextList": [
            {
              "content": "<span style='color: #888888;'>距您228m，杨浦区黄兴路221号互联宝地二期负1层B1-68</span>",
              "type": 0
            },
            {
              "content": "<span style='color: #888888;'>附近有<span style='color: #FF4B10;'>多家门店</span>，请确认取餐门店</span>",
              "type": 0
            }
          ],
          "tipList": []
        },
        "mopBrandInfoVO": {
          "brandId": "288",
          "mopBrandType": 20
        },
        "mopDealMappingInfoVO": {
          "mopDealMappingProductInfoVO": {
            "dealId": 1635198936,
            "dealIdStr": "1635198936",
            "dealTag": 1,
            "dealName": "【限量周边】联名光栅卡挂件双杯套餐",
            "mappingId": "2864067541",
            "dealMappingType": 30,
            "mopComboDishDataVO": {
              "comboProductId": "2312258382",
              "comboSkuId": "2864067541",
              "productType": 40,
              "comboName": "【限量周边】联名光栅卡挂件双杯套餐",
              "minPrice": "5200",
              "directAdd": false,
              "media": {
                "type": 60,
                "image": "<https://img.meituan.net/shopdirectconnectpic/abbbfba1279b01072e99fbb49537d64b.jpg>",
                "backgroundImage": "<http://p0.meituan.net/biztone/eebace0e4375a157dfbf6d285d04e56c4671.png@252w_252h_1e_1c>",
                "imageList": [
                  "<https://img.meituan.net/shopdirectconnectpic/582a75d2de7f0b9bfc5a7d54725f4a2a.jpg>"
                ]
              },
              "soldOut": false,
              "stockStatus": 2,
              "stock": -1,
              "comboDishGroupList": [
                {
                  "comboGroupName": "饮品",
                  "comboGroupId": "饮品-0",
                  "comboDishItemList": [
                    {
                      "spuId": "840935279",
                      "spuName": "生椰拿铁",
                      "skuIdList": [
                        "2873171508",
                        "2873171507",
                        "2873171509"
                      ],
                      "rank": 1,
                      "media": {
                        "type": 20,
                        "image": "<https://img.meituan.net/shopdirectconnectpic/3575dbfa0a59899724b5d906954873e7.jpg>",
                        "backgroundImage": "<http://p0.meituan.net/biztone/eebace0e4375a157dfbf6d285d04e56c4671.png@252w_252h_1e_1c>",
                        "imageList": [
                          "<https://img.meituan.net/shopdirectconnectpic/bf2e8038eb58a9796134ed2a21070709.jpg>"
                        ]
                      },
                      "soldOut": false,
                      "stockStatus": 2,
                      "spuStock": -1,
                      "currentPrice": "0",
                      "canCustomization": true,
                      "defaultChooseNum": 0,
                      "defaultChooseSku": {
                        "skuId": "2873171508",
                        "premiumList": [
                          {
                            "premiumId": "2540459141",
                            "selectNum": 1
                          },
                          {
                            "premiumId": "2540423644",
                            "selectNum": 1
                          },
                          {
                            "premiumId": "2540353556",
                            "selectNum": 1
                          },
                          {
                            "premiumId": "2540340500",
                            "selectNum": 1
                          }
                        ]
                      },
                      "needQi": true
                    },
                    {
                      "spuId": "2229378235",
                      "spuName": "小黄油拿铁",
                      "skuIdList": [
                        "2873141811",
                        "2873141813",
                        "2873141812"
                      ],
                      "rank": 2,
                      "media": {
                        "type": 20,
                        "image": "<https://img.meituan.net/shopdirectconnectpic/260e5f3d8a4a89e9869cbd8d9527d63f.jpg>",
                        "backgroundImage": "<http://p0.meituan.net/biztone/eebace0e4375a157dfbf6d285d04e56c4671.png@252w_252h_1e_1c>",
                        "imageList": [
                          "<https://img.meituan.net/shopdirectconnectpic/7a7ae382aa8ccb310ac3c520ab8c0770.jpg>"
                        ]
                      },
                      "soldOut": false,
                      "stockStatus": 2,
                      "spuStock": -1,
                      "currentPrice": "0",
                      "canCustomization": true,
                      "defaultChooseNum": 0,
                      "defaultChooseSku": {
                        "skuId": "2873141811",
                        "premiumList": [
                          {
                            "premiumId": "2540444295",
                            "selectNum": 1
                          },
                          {
                            "premiumId": "2540330704",
                            "selectNum": 1
                          },
                          {
                            "premiumId": "2540301874",
                            "selectNum": 1
                          },
                          {
                            "premiumId": "2540280964",
                            "selectNum": 1
                          }
                        ]
                      },
                      "needQi": true
                    },
                    {
                      "spuId": "2290264283",
                      "spuName": "苦瓜轻体果蔬茶",
                      "skuIdList": [
                        "2878647420",
                        "2878647421"
                      ],
                      "rank": 3,
                      "media": {
                        "type": 20,
                        "image": "<https://img.meituan.net/shopdirectconnectpic/1f1bc1a6bf89a59067b0d6b8928d33fa.jpg>",
                        "backgroundImage": "<http://p0.meituan.net/biztone/eebace0e4375a157dfbf6d285d04e56c4671.png@252w_252h_1e_1c>",
                        "imageList": [
                          "<https://img.meituan.net/shopdirectconnectpic/8e3a8ae3186bcd9d1454795ac047de81.jpg>"
                        ]
                      },
                      "soldOut": false,
                      "stockStatus": 2,
                      "spuStock": -1,
                      "currentPrice": "0",
                      "canCustomization": true,
                      "defaultChooseNum": 0,
                      "defaultChooseSku": {
                        "skuId": "2878647420",
                        "premiumList": [
                          {
                            "premiumId": "2559186640",
                            "selectNum": 1
                          },
                          {
                            "premiumId": "2566595052",
                            "selectNum": 1
                          },
                          {
                            "premiumId": "2559269700",
                            "selectNum": 1
                          }
                        ]
                      },
                      "needQi": false
                    },
                    {
                      "spuId": "2304702978",
                      "spuName": "冰吸生椰拿铁（首创）",
                      "skuIdList": [
                        "2878676656",
                        "2878676655"
                      ],
                      "rank": 4,
                      "media": {
                        "type": 20,
                        "image": "<https://img.meituan.net/shopdirectconnectpic/58a3183d01da56707b3652d362209189.jpg>",
                        "backgroundImage": "<http://p0.meituan.net/biztone/eebace0e4375a157dfbf6d285d04e56c4671.png@252w_252h_1e_1c>",
                        "imageList": [
                          "<https://img.meituan.net/shopdirectconnectpic/a99caf2fe40a179324b603b2ad14c607.jpg>"
                        ]
                      },
                      "soldOut": false,
                      "stockStatus": 2,
                      "spuStock": -1,
                      "currentPrice": "0",
                      "canCustomization": true,
                      "defaultChooseNum": 0,
                      "defaultChooseSku": {
                        "skuId": "2878676656",
                        "premiumList": [
                          {
                            "premiumId": "2559347768",
                            "selectNum": 1
                          },
                          {
                            "premiumId": "2559404566",
                            "selectNum": 1
                          },
                          {
                            "premiumId": "2559402655",
                            "selectNum": 1
                          },
                          {
                            "premiumId": "2559351882",
                            "selectNum": 1
                          }
                        ]
                      },
                      "needQi": true
                    },
                    {
                      "spuId": "2316930928",
                      "spuName": "陨石拿铁",
                      "skuIdList": [
                        "2878658750",
                        "2878658749"
                      ],
                      "rank": 5,
                      "media": {
                        "type": 20,
                        "image": "<https://img.meituan.net/shopdirectconnectpic/c619515c3563ee05a7ae72138b28ba62.jpg>",
                        "backgroundImage": "<http://p0.meituan.net/biztone/eebace0e4375a157dfbf6d285d04e56c4671.png@252w_252h_1e_1c>",
                        "imageList": [
                          "<https://img.meituan.net/shopdirectconnectpic/256630f40ae771533364d5dbfce38fa4.jpg>"
                        ]
                      },
                      "soldOut": false,
                      "stockStatus": 2,
                      "spuStock": -1,
                      "currentPrice": "0",
                      "canCustomization": true,
                      "defaultChooseNum": 0,
                      "defaultChooseSku": {
                        "skuId": "2878658750",
                        "premiumList": [
                          {
                            "premiumId": "2559210984",
                            "selectNum": 1
                          },
                          {
                            "premiumId": "2559242608",
                            "selectNum": 1
                          },
                          {
                            "premiumId": "2559333065",
                            "selectNum": 1
                          },
                          {
                            "premiumId": "2559376102",
                            "selectNum": 1
                          }
                        ]
                      },
                      "needQi": true
                    },
                    {
                      "spuId": "2317735733",
                      "spuName": "轻咖 柠檬茶（超大杯）",
                      "skuIdList": [
                        "2880849817"
                      ],
                      "rank": 6,
                      "media": {
                        "type": 20,
                        "image": "<https://img.meituan.net/shopdirectconnectpic/ee58ca72a73321f7cdfeeac0cc74b10b.jpg>",
                        "backgroundImage": "<http://p0.meituan.net/biztone/eebace0e4375a157dfbf6d285d04e56c4671.png@252w_252h_1e_1c>",
                        "imageList": [
                          "<https://img.meituan.net/shopdirectconnectpic/700536dfbd626c87485aabd497507030.jpg>"
                        ]
                      },
                      "soldOut": false,
                      "stockStatus": 2,
                      "spuStock": -1,
                      "currentPrice": "0",
                      "canCustomization": true,
                      "defaultChooseNum": 0,
                      "defaultChooseSku": {
                        "skuId": "2880849817",
                        "premiumList": [
                          {
                            "premiumId": "2565180779",
                            "selectNum": 1
                          },
                          {
                            "premiumId": "2565322176",
                            "selectNum": 1
                          },
                          {
                            "premiumId": "2565364149",
                            "selectNum": 1
                          },
                          {
                            "premiumId": "2565266242",
                            "selectNum": 1
                          }
                        ]
                      },
                      "needQi": false
                    },
                    {
                      "spuId": "841630645",
                      "spuName": "橙C美式",
                      "skuIdList": [
                        "2873155689",
                        "2873155688"
                      ],
                      "rank": 7,
                      "media": {
                        "type": 20,
                        "image": "<https://img.meituan.net/shopdirectconnectpic/853f61fcf4ceeee4da067ad73fdc5ef7.jpg>",
                        "backgroundImage": "<http://p0.meituan.net/biztone/eebace0e4375a157dfbf6d285d04e56c4671.png@252w_252h_1e_1c>",
                        "imageList": [
                          "<https://img.meituan.net/shopdirectconnectpic/0a656446e8100cbe0d183dd486ea9a8e.jpg>"
                        ]
                      },
                      "soldOut": false,
                      "stockStatus": 2,
                      "spuStock": -1,
                      "currentPrice": "0",
                      "canCustomization": true,
                      "defaultChooseNum": 0,
                      "defaultChooseSku": {
                        "skuId": "2873155689",
                        "premiumList": [
                          {
                            "premiumId": "2540410001",
                            "selectNum": 1
                          },
                          {
                            "premiumId": "2540338659",
                            "selectNum": 1
                          },
                          {
                            "premiumId": "2540338660",
                            "selectNum": 1
                          },
                          {
                            "premiumId": "2540397275",
                            "selectNum": 1
                          },
                          {
                            "premiumId": "2540353638",
                            "selectNum": 1
                          }
                        ]
                      },
                      "needQi": true
                    }
                  ],
                  "rank": 0,
                  "fixed": false,
                  "minChoiceNum": 2,
                  "maxChoiceNum": 2,
                  "repeatChooseNum": 2,
                  "showPrice": true
                },
                {
                  "comboGroupName": "周边",
                  "comboGroupId": "周边-1",
                  "comboDishItemList": [
                    {
                      "spuId": "2317597872",
                      "spuName": "光栅卡挂件·自嘲熊和朋友们系列",
                      "skuIdList": [
                        "2880906263"
                      ],
                      "rank": 1,
                      "media": {
                        "type": 20,
                        "image": "<https://img.meituan.net/shopdirectconnectpic/fd46d472ca2919616311af2fe0be12ea.jpg>",
                        "backgroundImage": "<http://p0.meituan.net/biztone/eebace0e4375a157dfbf6d285d04e56c4671.png@252w_252h_1e_1c>",
                        "imageList": [
                          "<https://img.meituan.net/shopdirectconnectpic/44fe3a42b4ce7511a046b52f1d992a06.jpg>"
                        ]
                      },
                      "soldOut": false,
                      "stockStatus": 1,
                      "spuStock": 5,
                      "currentPrice": "0",
                      "canCustomization": false,
                      "defaultChooseNum": 0,
                      "defaultChooseSku": {
                        "skuId": "2880906263",
                        "premiumList": []
                      },
                      "needQi": false
                    }
                  ],
                  "rank": 1,
                  "fixed": false,
                  "minChoiceNum": 1,
                  "maxChoiceNum": 1,
                  "repeatChooseNum": 1,
                  "showPrice": true
                }
              ],
              "extendInfoMap": {
                "COMBO_ADD_PRICE_WITH_RAW": "1"
              },
              "needQi": false
            }
          },
          "isSupport": true,
          "dealUpperLimit": 100,
          "skuUpperLimit": 15
        },
        "mopProductPriceVO": {
          "currentPrice": "3090",
          "mopCurrentPrice": "null",
          "dealCurrentPrice": "3090",
          "discountPrice": "4510",
          "totalPrice": "7600",
          "selectNum": 1,
          "dealTotalPrice": "7600",
          "dealDiscountPrice": "4510",
          "needQi": false
        },
        "currentPage": 10,
        "usePromotionDetails": [
          {
            "promoId": "685890111740298235",
            "promoType": 6,
            "totalDiscount": 300,
            "activityProductId": 11,
            "title": "神券-吃喝玩乐神券"
          }
        ]
      },
      "transferDataVO": {
        "transferData": {
          "quantity": "1"
        }
      },
      "giftInfoVO": {
        "canGive": false
      }
    },
    "success": true,
    "fail": false
  }
}
```

### 筛选后的精简响应

```
// 代码块
{
    "data": {
        "nodeDataMap": {
            "MopContainer": {
                "p": {
                    "onlineOrderPropsVo": {
                        "mopDealMappingInfoVO": {
                            "mopDealMappingProductInfoVO": {
                                "dealId": 1635198936,
                                "dealIdStr": "1635198936",
                                "dealTag": 1,
                                "dealName": "【限量周边】联名光栅卡挂件双杯套餐",
                                "mappingId": "2864067541",
                                "dealMappingType": 30,
                                "mopComboDishDataVO": {
                                    "comboProductId": "2312258382",
                                    "comboSkuId": "2864067541",
                                    "productType": 40,
                                    "comboName": "【限量周边】联名光栅卡挂件双杯套餐",
                                    "minPrice": "5200",
                                    "directAdd": false,
                                    "media": {
                                        "type": 60,
                                        "image": "<https://img.meituan.net/shopdirectconnectpic/abbbfba1279b01072e99fbb49537d64b.jpg>",
                                        "backgroundImage": "<http://p0.meituan.net/biztone/eebace0e4375a157dfbf6d285d04e56c4671.png@252w_252h_1e_1c>",
                                        "imageList": [
                                            "<https://img.meituan.net/shopdirectconnectpic/582a75d2de7f0b9bfc5a7d54725f4a2a.jpg>"
                                        ]
                                    },
                                    "soldOut": false,
                                    "stockStatus": 2,
                                    "stock": -1,
                                    "comboDishGroupList": [
                                        {
                                            "comboGroupName": "饮品",
                                            "comboGroupId": "饮品-0",
                                            "comboDishItemList": [
                                                {
                                                    "spuId": "840935279",
                                                    "spuName": "生椰拿铁",
                                                    "skuIdList": [
                                                        "2873171508",
                                                        "2873171507",
                                                        "2873171509"
                                                    ],
                                                    "rank": 1,
                                                    "media": {
                                                        "type": 20,
                                                        "image": "<https://img.meituan.net/shopdirectconnectpic/3575dbfa0a59899724b5d906954873e7.jpg>",
                                                        "backgroundImage": "<http://p0.meituan.net/biztone/eebace0e4375a157dfbf6d285d04e56c4671.png@252w_252h_1e_1c>",
                                                        "imageList": [
                                                            "<https://img.meituan.net/shopdirectconnectpic/bf2e8038eb58a9796134ed2a21070709.jpg>"
                                                        ]
                                                    },
                                                    "soldOut": false,
                                                    "stockStatus": 2,
                                                    "spuStock": -1,
                                                    "currentPrice": "0",
                                                    "canCustomization": true,
                                                    "defaultChooseNum": 0,
                                                    "defaultChooseSku": {
                                                        "skuId": "2873171508",
                                                        "premiumList": [
                                                            {
                                                                "premiumId": "2540459141",
                                                                "selectNum": 1
                                                            },
                                                            {
                                                                "premiumId": "2540423644",
                                                                "selectNum": 1
                                                            },
                                                            {
                                                                "premiumId": "2540353556",
                                                                "selectNum": 1
                                                            },
                                                            {
                                                                "premiumId": "2540340500",
                                                                "selectNum": 1
                                                            }
                                                        ]
                                                    },
                                                    "needQi": true
                                                },
                                                {
                                                    "spuId": "2229378235",
                                                    "spuName": "小黄油拿铁",
                                                    "skuIdList": [
                                                        "2873141811",
                                                        "2873141813",
                                                        "2873141812"
                                                    ],
                                                    "rank": 2,
                                                    "media": {
                                                        "type": 20,
                                                        "image": "<https://img.meituan.net/shopdirectconnectpic/260e5f3d8a4a89e9869cbd8d9527d63f.jpg>",
                                                        "backgroundImage": "<http://p0.meituan.net/biztone/eebace0e4375a157dfbf6d285d04e56c4671.png@252w_252h_1e_1c>",
                                                        "imageList": [
                                                            "<https://img.meituan.net/shopdirectconnectpic/7a7ae382aa8ccb310ac3c520ab8c0770.jpg>"
                                                        ]
                                                    },
                                                    "soldOut": false,
                                                    "stockStatus": 2,
                                                    "spuStock": -1,
                                                    "currentPrice": "0",
                                                    "canCustomization": true,
                                                    "defaultChooseNum": 0,
                                                    "defaultChooseSku": {
                                                        "skuId": "2873141811",
                                                        "premiumList": [
                                                            {
                                                                "premiumId": "2540444295",
                                                                "selectNum": 1
                                                            },
                                                            {
                                                                "premiumId": "2540330704",
                                                                "selectNum": 1
                                                            },
                                                            {
                                                                "premiumId": "2540301874",
                                                                "selectNum": 1
                                                            },
                                                            {
                                                                "premiumId": "2540280964",
                                                                "selectNum": 1
                                                            }
                                                        ]
                                                    },
                                                    "needQi": true
                                                },
                                                {
                                                    "spuId": "2290264283",
                                                    "spuName": "苦瓜轻体果蔬茶",
                                                    "skuIdList": [
                                                        "2878647420",
                                                        "2878647421"
                                                    ],
                                                    "rank": 3,
                                                    "media": {
                                                        "type": 20,
                                                        "image": "<https://img.meituan.net/shopdirectconnectpic/1f1bc1a6bf89a59067b0d6b8928d33fa.jpg>",
                                                        "backgroundImage": "<http://p0.meituan.net/biztone/eebace0e4375a157dfbf6d285d04e56c4671.png@252w_252h_1e_1c>",
                                                        "imageList": [
                                                            "<https://img.meituan.net/shopdirectconnectpic/8e3a8ae3186bcd9d1454795ac047de81.jpg>"
                                                        ]
                                                    },
                                                    "soldOut": false,
                                                    "stockStatus": 2,
                                                    "spuStock": -1,
                                                    "currentPrice": "0",
                                                    "canCustomization": true,
                                                    "defaultChooseNum": 0,
                                                    "defaultChooseSku": {
                                                        "skuId": "2878647420",
                                                        "premiumList": [
                                                            {
                                                                "premiumId": "2559186640",
                                                                "selectNum": 1
                                                            },
                                                            {
                                                                "premiumId": "2566595052",
                                                                "selectNum": 1
                                                            },
                                                            {
                                                                "premiumId": "2559269700",
                                                                "selectNum": 1
                                                            }
                                                        ]
                                                    },
                                                    "needQi": false
                                                },
                                                {
                                                    "spuId": "2304702978",
                                                    "spuName": "冰吸生椰拿铁（首创）",
                                                    "skuIdList": [
                                                        "2878676656",
                                                        "2878676655"
                                                    ],
                                                    "rank": 4,
                                                    "media": {
                                                        "type": 20,
                                                        "image": "<https://img.meituan.net/shopdirectconnectpic/58a3183d01da56707b3652d362209189.jpg>",
                                                        "backgroundImage": "<http://p0.meituan.net/biztone/eebace0e4375a157dfbf6d285d04e56c4671.png@252w_252h_1e_1c>",
                                                        "imageList": [
                                                            "<https://img.meituan.net/shopdirectconnectpic/a99caf2fe40a179324b603b2ad14c607.jpg>"
                                                        ]
                                                    },
                                                    "soldOut": false,
                                                    "stockStatus": 2,
                                                    "spuStock": -1,
                                                    "currentPrice": "0",
                                                    "canCustomization": true,
                                                    "defaultChooseNum": 0,
                                                    "defaultChooseSku": {
                                                        "skuId": "2878676656",
                                                        "premiumList": [
                                                            {
                                                                "premiumId": "2559347768",
                                                                "selectNum": 1
                                                            },
                                                            {
                                                                "premiumId": "2559404566",
                                                                "selectNum": 1
                                                            },
                                                            {
                                                                "premiumId": "2559402655",
                                                                "selectNum": 1
                                                            },
                                                            {
                                                                "premiumId": "2559351882",
                                                                "selectNum": 1
                                                            }
                                                        ]
                                                    },
                                                    "needQi": true
                                                },
                                                {
                                                    "spuId": "2316930928",
                                                    "spuName": "陨石拿铁",
                                                    "skuIdList": [
                                                        "2878658750",
                                                        "2878658749"
                                                    ],
                                                    "rank": 5,
                                                    "media": {
                                                        "type": 20,
                                                        "image": "<https://img.meituan.net/shopdirectconnectpic/c619515c3563ee05a7ae72138b28ba62.jpg>",
                                                        "backgroundImage": "<http://p0.meituan.net/biztone/eebace0e4375a157dfbf6d285d04e56c4671.png@252w_252h_1e_1c>",
                                                        "imageList": [
                                                            "<https://img.meituan.net/shopdirectconnectpic/256630f40ae771533364d5dbfce38fa4.jpg>"
                                                        ]
                                                    },
                                                    "soldOut": false,
                                                    "stockStatus": 2,
                                                    "spuStock": -1,
                                                    "currentPrice": "0",
                                                    "canCustomization": true,
                                                    "defaultChooseNum": 0,
                                                    "defaultChooseSku": {
                                                        "skuId": "2878658750",
                                                        "premiumList": [
                                                            {
                                                                "premiumId": "2559210984",
                                                                "selectNum": 1
                                                            },
                                                            {
                                                                "premiumId": "2559242608",
                                                                "selectNum": 1
                                                            },
                                                            {
                                                                "premiumId": "2559333065",
                                                                "selectNum": 1
                                                            },
                                                            {
                                                                "premiumId": "2559376102",
                                                                "selectNum": 1
                                                            }
                                                        ]
                                                    },
                                                    "needQi": true
                                                },
                                                {
                                                    "spuId": "2317735733",
                                                    "spuName": "轻咖 柠檬茶（超大杯）",
                                                    "skuIdList": [
                                                        "2880849817"
                                                    ],
                                                    "rank": 6,
                                                    "media": {
                                                        "type": 20,
                                                        "image": "<https://img.meituan.net/shopdirectconnectpic/ee58ca72a73321f7cdfeeac0cc74b10b.jpg>",
                                                        "backgroundImage": "<http://p0.meituan.net/biztone/eebace0e4375a157dfbf6d285d04e56c4671.png@252w_252h_1e_1c>",
                                                        "imageList": [
                                                            "<https://img.meituan.net/shopdirectconnectpic/700536dfbd626c87485aabd497507030.jpg>"
                                                        ]
                                                    },
                                                    "soldOut": false,
                                                    "stockStatus": 2,
                                                    "spuStock": -1,
                                                    "currentPrice": "0",
                                                    "canCustomization": true,
                                                    "defaultChooseNum": 0,
                                                    "defaultChooseSku": {
                                                        "skuId": "2880849817",
                                                        "premiumList": [
                                                            {
                                                                "premiumId": "2565180779",
                                                                "selectNum": 1
                                                            },
                                                            {
                                                                "premiumId": "2565322176",
                                                                "selectNum": 1
                                                            },
                                                            {
                                                                "premiumId": "2565364149",
                                                                "selectNum": 1
                                                            },
                                                            {
                                                                "premiumId": "2565266242",
                                                                "selectNum": 1
                                                            }
                                                        ]
                                                    },
                                                    "needQi": false
                                                },
                                                {
                                                    "spuId": "841630645",
                                                    "spuName": "橙C美式",
                                                    "skuIdList": [
                                                        "2873155689",
                                                        "2873155688"
                                                    ],
                                                    "rank": 7,
                                                    "media": {
                                                        "type": 20,
                                                        "image": "<https://img.meituan.net/shopdirectconnectpic/853f61fcf4ceeee4da067ad73fdc5ef7.jpg>",
                                                        "backgroundImage": "<http://p0.meituan.net/biztone/eebace0e4375a157dfbf6d285d04e56c4671.png@252w_252h_1e_1c>",
                                                        "imageList": [
                                                            "<https://img.meituan.net/shopdirectconnectpic/0a656446e8100cbe0d183dd486ea9a8e.jpg>"
                                                        ]
                                                    },
                                                    "soldOut": false,
                                                    "stockStatus": 2,
                                                    "spuStock": -1,
                                                    "currentPrice": "0",
                                                    "canCustomization": true,
                                                    "defaultChooseNum": 0,
                                                    "defaultChooseSku": {
                                                        "skuId": "2873155689",
                                                        "premiumList": [
                                                            {
                                                                "premiumId": "2540410001",
                                                                "selectNum": 1
                                                            },
                                                            {
                                                                "premiumId": "2540338659",
                                                                "selectNum": 1
                                                            },
                                                            {
                                                                "premiumId": "2540338660",
                                                                "selectNum": 1
                                                            },
                                                            {
                                                                "premiumId": "2540397275",
                                                                "selectNum": 1
                                                            },
                                                            {
                                                                "premiumId": "2540353638",
                                                                "selectNum": 1
                                                            }
                                                        ]
                                                    },
                                                    "needQi": true
                                                }
                                            ],
                                            "rank": 0,
                                            "fixed": false,
                                            "minChoiceNum": 2,
                                            "maxChoiceNum": 2,
                                            "repeatChooseNum": 2,
                                            "showPrice": true
                                        },
                                        {
                                            "comboGroupName": "周边",
                                            "comboGroupId": "周边-1",
                                            "comboDishItemList": [
                                                {
                                                    "spuId": "2317597872",
                                                    "spuName": "光栅卡挂件·自嘲熊和朋友们系列",
                                                    "skuIdList": [
                                                        "2880906263"
                                                    ],
                                                    "rank": 1,
                                                    "media": {
                                                        "type": 20,
                                                        "image": "<https://img.meituan.net/shopdirectconnectpic/fd46d472ca2919616311af2fe0be12ea.jpg>",
                                                        "backgroundImage": "<http://p0.meituan.net/biztone/eebace0e4375a157dfbf6d285d04e56c4671.png@252w_252h_1e_1c>",
                                                        "imageList": [
                                                            "<https://img.meituan.net/shopdirectconnectpic/44fe3a42b4ce7511a046b52f1d992a06.jpg>"
                                                        ]
                                                    },
                                                    "soldOut": false,
                                                    "stockStatus": 1,
                                                    "spuStock": 5,
                                                    "currentPrice": "0",
                                                    "canCustomization": false,
                                                    "defaultChooseNum": 0,
                                                    "defaultChooseSku": {
                                                        "skuId": "2880906263",
                                                        "premiumList": []
                                                    },
                                                    "needQi": false
                                                }
                                            ],
                                            "rank": 1,
                                            "fixed": false,
                                            "minChoiceNum": 1,
                                            "maxChoiceNum": 1,
                                            "repeatChooseNum": 1,
                                            "showPrice": true
                                        }
                                    ],
                                    "extendInfoMap": {
                                        "COMBO_ADD_PRICE_WITH_RAW": "1"
                                    },
                                    "needQi": false
                                }
                            }
                        },
                        "mopProductPriceVO": {
                            "currentPrice": "3090",
                            "mopCurrentPrice": "null",
                            "dealCurrentPrice": "3090",
                            "discountPrice": "4510",
                            "totalPrice": "7600",
                            "selectNum": 1,
                            "dealTotalPrice": "7600",
                            "dealDiscountPrice": "4510",
                            "needQi": false
                        },
                        "currentPage": 10,
                        "usePromotionDetails": [
                            {
                                "promoId": "685890111740298235",
                                "promoType": 6,
                                "totalDiscount": 300,
                                "activityProductId": 11,
                                "title": "神券-吃喝玩乐神券"
                            }
                        ]
                    }
                },
                "s": {
                    "wrapCardStyle": {
                        "position": "relative",
                        "zIndex": 1
                    }
                },
                "pc": {
                    "mopTempCartTempProductList": {
                        "r": true
                    }
                },
                "e": {
                    "e": {
                        "onSubmitSuccess": [
                            {
                                "n": "BottomBar",
                                "e": "onSubmitSuccess",
                                "t": [
                                    {
                                        "t": "",
                                        "f": ""
                                    }
                                ]
                            }
                        ]
                    }
                }
            },
            "MopDataContainer": {
                "i": "430",
                "p": {
                    "quantity": "1"
                },
                "s": {
                    "wrapStyle": {
                        "marginRight": 0,
                        "marginLeft": 0
                    }
                },
                "pc": {
                    "quantity": {
                        "r": true
                    },
                    "mopTempData": {
                        "r": true
                    }
                }
            },
            "AfterPay": {
                "i": "132",
                "t": "l",
                "p": {
                    "afterPayList": [],
                    "tailTips": [],
                    "lx": {
                        "channelName": "meishi",
                        "pageInfoKey": "group-order-submit",
                        "commonParams": {
                            "is_mvp": "0",
                            "deal_id": "1635198936",
                            "poi_id": "1851844943",
                            "tab_name": 0,
                            "is_distribute": 0,
                            "source": "-999",
                            "scene_type": "1",
                            "deal_sale_count": -999,
                            "deal_count": "-999",
                            "distribute_deal_count": -999,
                            "bundle_product_source": 0,
                            "page_version": "2",
                            "page_module": "0",
                            "has_text": 0,
                            "submit_deal_info": "-999",
                            "is_person_order_same_phone_number": 0,
                            "is_person_login_same_phone_number": 0,
                            "is_null": 1
                        },
                        "cid": "c_meishi_rao5v99i",
                        "insurance_mc": {
                            "bid": "b_meishi_h0kdj3z1_mc",
                            "valLab": {
                                "poi_id": "-999"
                            }
                        },
                        "insurance_mv": {
                            "bid": "b_meishi_h0kdj3z1_mv",
                            "valLab": {
                                "poi_id": "-999"
                            }
                        },
                        "full_rebate_mv": {
                            "bid": "b_meishi_hk57o0vx_mv",
                            "valLab": {
                                "activity_id": [],
                                "page_version": "2"
                            }
                        },
                        "full_rebate_mc": {
                            "bid": "b_meishi_hk57o0vx_mc",
                            "valLab": {
                                "activity_id": [],
                                "page_version": "2"
                            }
                        },
                        "coupon_return_mv": {
                            "bid": "b_meishi_vfisf00l_mv"
                        }
                    },
                    "isTetuan": false
                },
                "s": {
                    "cardWrapStyle": {
                        "marginBottom": 0
                    }
                },
                "pc": {
                    "afterPayList": {
                        "r": true
                    }
                }
            },
            "BottomFill": {
                "i": "509",
                "t": "l",
                "p": {
                    "full": false
                }
            },
            "DzBgLineargradient": {
                "i": "239",
                "t": "l",
                "p": {
                    "start": {
                        "x": 0,
                        "y": 0
                    },
                    "end": {
                        "x": 0,
                        "y": 1
                    },
                    "colors": [
                        "#FFFFFF",
                        "#F4F4F4"
                    ]
                },
                "s": {
                    "wrapCardStyle": {
                        "top": 43,
                        "left": 0,
                        "bottom": 0,
                        "position": "absolute",
                        "right": 0,
                        "height": 150,
                        "zIndex": 0
                    }
                }
            },
            "MaxLeezCard": {
                "i": "37",
                "s": {
                    "style": {
                        "padding": 0,
                        "margin": 0,
                        "backgroundColor": "#f7f7f7",
                        "paddingBottom": 0,
                        "top": 0,
                        "left": 0,
                        "bottom": 0,
                        "paddingRight": 0,
                        "paddingTop": 0,
                        "position": "absolute",
                        "right": 0,
                        "paddingLeft": 0
                    }
                }
            },
            "MaxLeezCard1": {
                "i": "37",
                "s": {
                    "style": {
                        "padding": 0,
                        "backgroundColor": "#ffffff",
                        "right": 0,
                        "borderRadius": 0,
                        "left": 0,
                        "height": 100
                    }
                }
            },
            "DzBgLineargradient2": {
                "i": "239",
                "t": "l",
                "p": {
                    "start": {
                        "x": 0,
                        "y": 0
                    },
                    "end": {
                        "x": 0,
                        "y": 1
                    },
                    "colors": [
                        "#FFFFFF",
                        "#F4F4F4"
                    ]
                },
                "s": {
                    "wrapCardStyle": {
                        "position": "relative",
                        "right": 0,
                        "left": 0,
                        "height": 100
                    }
                }
            },
            "TopTag": {
                "i": "155",
                "t": "l",
                "p": {
                    "labelList": [],
                    "closeEmitKey": "CLOSE_POP_SLIDER_MODAL",
                    "lx": {
                        "channelName": "meishi",
                        "pageInfoKey": "group-order-submit",
                        "commonParams": {
                            "is_mvp": "0",
                            "deal_id": "1635198936",
                            "poi_id": "1851844943",
                            "tab_name": 0,
                            "is_distribute": 0,
                            "source": "-999",
                            "scene_type": "1",
                            "deal_sale_count": -999,
                            "deal_count": "-999",
                            "distribute_deal_count": -999,
                            "bundle_product_source": 0,
                            "page_version": "2",
                            "page_module": "0",
                            "has_text": 0,
                            "submit_deal_info": "-999",
                            "is_person_order_same_phone_number": 0,
                            "is_person_login_same_phone_number": 0,
                            "is_null": 1
                        },
                        "cid": "c_meishi_rao5v99i",
                        "closeMc": {
                            "bid": "b_meishi_byrm830y_mc"
                        },
                        "valLab": {
                            "status": 0,
                            "tab_name": "秒提·到店取",
                            "deal_id": "1635198936",
                            "poi_id": "1851844943",
                            "mode_type": 2
                        }
                    },
                    "labels": [],
                    "closeVisible": true,
                    "full": false
                },
                "s": {
                    "wrapCardStyle": {
                        "marginBottom": 13
                    }
                }
            },
            "Dialog": {
                "i": "142",
                "t": "l",
                "p": {
                    "reportTags": {
                        "errCode": 0,
                        "errMsg": "成功",
                        "errUserMsg": "成功",
                        "dpWX": false,
                        "mtWX": false,
                        "source": "food-poi",
                        "routeByPortm": "0"
                    },
                    "isFoodPopBack": true,
                    "lx": {
                        "channelName": "meishi",
                        "pageInfoKey": "group-order-submit",
                        "commonParams": {
                            "is_mvp": "0",
                            "deal_id": "1635198936",
                            "poi_id": "1851844943",
                            "tab_name": 0,
                            "is_distribute": 0,
                            "source": "-999",
                            "scene_type": "1",
                            "deal_sale_count": -999,
                            "deal_count": "-999",
                            "distribute_deal_count": -999,
                            "bundle_product_source": 0,
                            "page_version": "2",
                            "page_module": "0",
                            "has_text": 0,
                            "submit_deal_info": "-999",
                            "is_person_order_same_phone_number": 0,
                            "is_person_login_same_phone_number": 0,
                            "is_null": 1
                        },
                        "cid": "c_meishi_rao5v99i",
                        "module_mv": {
                            "bid": "b_meishi_lvzq6i2d_mv"
                        },
                        "confirm_mc": {
                            "bid": "b_meishi_zv9z65nj_mc"
                        },
                        "valLab": {
                            "card_id": "",
                            "title": "成功"
                        }
                    },
                    "reportMsg": "",
                    "scene": "food-order-submit-add"
                },
                "e": {
                    "e": {
                        "onReload": [
                            {
                                "n": "MeishiCommonDuoLifecycle1",
                                "e": "update"
                            }
                        ]
                    }
                }
            },
            "MeishiKaMopDuoSubmitRemindModal": {
                "i": "642",
                "p": {},
                "e": {
                    "e": {
                        "onReload": [
                            {
                                "n": "MeishiCommonDuoLifecycle1",
                                "e": "update"
                            }
                        ]
                    }
                }
            },
            "MeishiKaMopCheckShopModal": {
                "i": "403",
                "p": {
                    "buyScene": "1",
                    "pageQuery": {
                        "mrn_transparent": "true",
                        "mrn_biz": "meishi",
                        "mrn_entry": "c-group-order-submit",
                        "tabType": "5",
                        "nibBizConsistency": "gmV2peeKZ5C2xJqoC9o14IlfIQJKqkO42Jf4ABsGz-8KD454ZUT648SFJb5Xmlo-tSFK7mzIGLe9XMWA2Gt70lqnXoh_w-Ie4GlDqMzVbsILHK32-TwlhfYua1xXe04oGaK6dN6Wd6iqiBtzdh_feoZSXeCLumIVI8-FFsw5IPUd5gp7A-VOgaJUWSNCZwET0yUZRs0yqKhc-jKVtIaNIE4vuEIgMJur7tFe--Ua7tcBIGYNj3Rrq8B75n3Z9Zf6o1C3qmDlDxCEZzaULtTx2JQ-Q-7e_98y5sNaY7LgBx4",
                        "trafficSourceActivityId": "",
                        "sec_source": "rhhj_dd",
                        "isOnlyShowShopCart": "false",
                        "mrn_component": "GroupOrderSubmit",
                        "isDealJudge": "",
                        "_referer": "food-poi",
                        "flexibleJSON": "{\\"assignProm\\":[]}",
                        "mrn_hideNextNavBar": "true",
                        "hideLoading": "true",
                        "groupBuyMopScene": "1",
                        "hasKNBParams": "1",
                        "venueId": "",
                        "mlive_ext": "",
                        "buyPoiIdEncrypt": "qB4r17707da606bc98ea64a037925971660ee8e63d7690a06106e1ce2a76ee607d88922f49ead8b8b2b7712a292610e43d2bac167cdcda7719f50f20vxu5",
                        "source": "",
                        "mrn_adjustParentFrame": "true",
                        "productType": "",
                        "dealId": "1635198936",
                        "lng": "121.52897062950872",
                        "halfScreenSubmitHeight": "0.85",
                        "payPrice": "30.9",
                        "showPrice": "30.9",
                        "shelfFusion": "true",
                        "lat": "31.273660438522672",
                        "dd_source": "",
                        "mrn_hideloading": "true",
                        "govPromotion": "",
                        "isTransparent": "true",
                        "buyPoiId": "1851844943",
                        "mrn_min_version": "2.115.0",
                        "campaignId": ""
                    },
                    "chooseShopUrl": "imeituan://www.meituan.com/mrn?mrn_biz=meishi&mrn_entry=ka-mop-poi-select&mrn_component=kaMopPoiSelect&dishSource=10&shopId=1851844943&dealId=1635198936&brandId=288&jumpToShopSelectPageOnLoad=true&pageSource=instant-order-page",
                    "disableSwitchShop": false,
                    "location": {
                        "lat": "31.273660438522672",
                        "lng": "121.52897062950872",
                        "accuracy": 9.195289588725755
                    },
                    "isFromTetuan": false
                },
                "e": {
                    "e": {
                        "onSwitchShop": [
                            {
                                "n": "MeishiCommonDuoLifecycle1",
                                "e": "update"
                            }
                        ],
                        "onConfirmOrder": [
                            {
                                "n": "BottomBar",
                                "e": "onMiaoTiSubmitPress",
                                "t": [
                                    {
                                        "t": "miaoTiConfirm",
                                        "f": ""
                                    }
                                ]
                            }
                        ]
                    }
                }
            },
            "SubmitRisk": {
                "i": "192",
                "p": {
                    "yodaEnv": "Prod",
                    "lx": [],
                    "yodaRequestParams": {
                        "os": "ios",
                        "platform": "mt",
                        "version": "12.56.200",
                        "uuid": "00000000000007A0030108A0C430C88DF8E7BA59BF348A177457840783633080",
                        "userId": "3842765890",
                        "token": "AgFsIpe7YXQee_IBR4ln-oXXq_F6jtq2AOMT_6oEuvwbZm3IQkWpq9RK7ZiTZb-EXRonInIFDWyzYAAAAAAENAAA2w_Qkp6xP7nbBz0_CIKZwutJA8YJUz3UHNqjoIPrlkhqnK4I_I3ifwXnnfUT-7KV"
                    }
                },
                "e": {
                    "e": {
                        "onSurePress": [
                            {
                                "n": "BottomBar",
                                "e": "onSubmitPress",
                                "t": [
                                    {
                                        "t": "sType",
                                        "f": ""
                                    }
                                ]
                            }
                        ]
                    }
                }
            },
            "MeishiFoodGroupSubmitLogic": {
                "i": "248",
                "p": {
                    "dealId": "1635198936",
                    "CID": "c_meishi_rao5v99i"
                }
            },
            "FoodSubmitStatic": {
                "i": "1090"
            },
            "MeishiCommonDuoLifecycle1": {
                "i": "13",
                "e": {
                    "e": {
                        "preview.onEngineFail": [
                            {
                                "n": "FoodSubmitStatic",
                                "e": "onPreviewEngineFail"
                            }
                        ],
                        "preview.onResponse": [
                            {
                                "n": "FoodSubmitStatic",
                                "e": "onPreviewResponse"
                            }
                        ],
                        "submit.onFail": [
                            {
                                "n": "SubmitRisk",
                                "e": "onRiskDialogShow",
                                "t": [
                                    {
                                        "t": "item",
                                        "f": "item"
                                    }
                                ]
                            }
                        ],
                        "preview.onSuccess": [
                            {
                                "n": "MeishiCommonEventNav1",
                                "e": "setWebDocumentTitle",
                                "p": {
                                    "title": "提交订单"
                                }
                            }
                        ]
                    }
                }
            },
            "MeishiCommonEventNav1": {
                "i": "90"
            },
            "MeishiUtilAutoReporterInstance1": {
                "i": "91"
            },
            "MeishiCommonEventLx1": {
                "i": "16"
            }
        },
        "currentData": {
            "poiName": "瑞幸咖啡（互联宝地二期店）"
        },
        "minifyHttpResponse": 1
    },
    "bizReq": {
        "bizCode": "nib.food.groupbuy",
        "environmentParam": {
            "duoCommonParam": {
                "location": {
                    "lat": 31.273660438522672,
                    "lng": 121.52897062950872,
                    "accuracy": 9.195289588725755
                },
                "userInfo": {
                    "userId": "3842765890",
                    "token": "AgFsIpe7YXQee_IBR4ln-oXXq_F6jtq2AOMT_6oEuvwbZm3IQkWpq9RK7ZiTZb-EXRonInIFDWyzYAAAAAAENAAA2w_Qkp6xP7nbBz0_CIKZwutJA8YJUz3UHNqjoIPrlkhqnK4I_I3ifwXnnfUT-7KV",
                    "uuid": "00000000000007A0030108A0C430C88DF8E7BA59BF348A177457840783633080",
                    "uuidV2": "00000000000007A0030108A0C430C88DF8E7BA59BF348A177457840783633080",
                    "mtuuid": "00000000000007A0030108A0C430C88DF8E7BA59BF348A177457840783633080",
                    "userAgent": "com.meituan.imeituan-beta/318515 (unknown, iOS 26.3.1, iPhone, Scale/3.000000)",
                    "userIp": "203.76.219.196",
                    "userIpV2": "103.202.145.196",
                    "unionId": "8b854f09f2814f2cb120f473ac3930eea176350111025506278",
                    "dpid": "",
                    "regionId": "1000330700"
                },
                "cityInfo": {
                    "cityId": "10",
                    "locCityId": "10"
                },
                "systemInfo": {
                    "version": "12.56.200",
                    "systemVersion": "26.3.1",
                    "device": "",
                    "platform": "ios",
                    "isWeb": false,
                    "isWeChatMiniProgram": false,
                    "isDebug": false,
                    "isMRN": true,
                    "mpAppId": "",
                    "envInWeb": {},
                    "utmInfo": {
                        "source": "Alpha",
                        "medium": "iphone",
                        "term": "12.56.200",
                        "content": "00000000000007A0030108A0C430C88DF8E7BA59BF348A177457840783633080",
                        "campaign": "AgroupBgroupD200Ghomepage_searchH0"
                    },
                    "mpAppVersion": "",
                    "mpPluginAppId": "",
                    "mtgsig": "{\\"a0\\":\\"3.0\\",\\"a1\\":\\"bb459669-615c-4dcd-a201-8dc32aa1b5e4\\",\\"a3\\":25,\\"a4\\":1777022673,\\"a5\\":\\"hjFa4G1f/VdV0QxxLR2f9WHuRUomdP9xFLSO9SOaerBZnSTM2fvaE9Y5HQ3K5BvEij/+VaG1bE9uZY2oq0N2RYCJAWr4Wkytv3z985HEGkYkeR4Vv1SKmys2Ffi/rcGHizZg33VnjSkIa13/lwVlX/emrv+FvK71ijX7Y7Qt2QoV4e0bi7n/bPlVCW0VA4XMTwBAX/4HkG9nfAEZuBBSBTPluM1Zz9iEQL1yX85vZ3+2jLSWV/ktQyxVI+w8nnIuCsLhPqYFaWG46BTjbRT0u2VtTnkZGd5H1GfOyu80NGrV3qmFgx3Ee3A8f2cZArlgxmfxib+bQU8tgw8UEuOjaj5mv/mjZaByWxi4K2AtMUIlXpzFuJzcl17gVISmNTx8mVzAXLMh7g==\\",\\"a6\\":0,\\"a7\\":\\"Nd4AWv4k0Fx0fpkpQ5vyLWJvwRn2izg1Ny1qe09UlJFKrLcc2tsxUqx4d3eG57Xkb2m7z+hX/hdHVooBtZn3Gbl/hBI/W/v7d+hpgBVFl7M=\\",\\"a8\\":\\"5395074119b4b9a92eaca0858e8c71ddf177f128cf6ee8e411d4f76a\\",\\"a9\\":\\"90deb76d5u1dX1sQuT8XDdFN97BTu6Xd7AeuzOzWPXsVm0B7bQ+Tzs8DFI1+gfMCu6WVv2d6wX5gJqgxS8nl4ffVfgkSWsHSjeLqc/qMMWiflDHCNqtv3SidUdGgjtWqO19IEzp/Jfj6OFEWTTbLZBvo8UR4OTQ9yIktavtwLf206SwiVzf2GrrKCoJaM91PQF6n3RDknPT09R2+ACHi6lV5VoPdBdyF99EAeI9GzgFC3cEaEs3vMUQspix7ztVbyjGCs7uB/P3ys3IdFmcMk3Mt4nsy+KP3v7ssral/s8AV6zt6xt+IfJhmQDXUocrCHMoyIHteGteTMS/OPaf90qpijbcsDkdW9onLsssUUMzIvTXFPIjtcvaMIEvUsKuu3JS5s9LO4x52fH1aiH0FHiy9NbZ3/I62QSo9gdQEplh26+esyVPxzgon0Smqj6AhH+IrfMtkZEosbTqK+TOWt6kYjuAy6nLAOiFNy+QC4QQqEEJ+HPVjVsFoNYZLEyUwG+TDkG1ftGcuGv68Z/jEjZv8/chjVOlIsd+RSXIQWAqoCFS/pdMNpsGgwJ3jD/fRA8Uj/XcTOuI5w14qyf412tcwWA/XP9LEp09VdXqNezbfXVnuUKaHuecum6RDUSeRXSWws4Zu2Wf6kXotabhgofNVnz8FFd3hY96yfkM0Gjl9Wns5r9A=\\",\\"a10\\":\\"5,202,1.1.6\\",\\"x0\\":2,\\"a2\\":\\"2ff86aeccfb8ae2ed76ec2d8dbbcb779\\"}",
                    "is_HOTEL": false,
                    "is_DP": false,
                    "is_MT": true
                },
                "fingerprint": {
                    "fingerprint": ""
                },
                "storage": {}
            },
            "submitVersion": "12.31.000",
            "pageId": 0,
            "gpsCoordinateType": "GCJ02",
            "magicMemberComponentVersion": "0.3.0"
        },
        "productParam": {
            "productId": "1635198936",
            "quantity": 1
        },
        "poiParam": {
            "poiId": "1851844943"
        },
        "merchantMemberParam": {
            "forcePut": 1
        },
        "payParam": {
            "payType": 0,
            "cashierEnvParam": "{}"
        },
        "promoParam": {
            "operatorPromoType": "0",
            "queryPromoLimitType": 0
        },
        "riskParam": {
            "erasePromotionType": 0,
            "yodaInfo": {}
        },
        "pageUrl": "{\\"mrn_transparent\\":\\"true\\",\\"mrn_biz\\":\\"meishi\\",\\"mrn_entry\\":\\"c-group-order-submit\\",\\"tabType\\":\\"5\\",\\"nibBizConsistency\\":\\"gmV2peeKZ5C2xJqoC9o14IlfIQJKqkO42Jf4ABsGz-8KD454ZUT648SFJb5Xmlo-tSFK7mzIGLe9XMWA2Gt70lqnXoh_w-Ie4GlDqMzVbsILHK32-TwlhfYua1xXe04oGaK6dN6Wd6iqiBtzdh_feoZSXeCLumIVI8-FFsw5IPUd5gp7A-VOgaJUWSNCZwET0yUZRs0yqKhc-jKVtIaNIE4vuEIgMJur7tFe--Ua7tcBIGYNj3Rrq8B75n3Z9Zf6o1C3qmDlDxCEZzaULtTx2JQ-Q-7e_98y5sNaY7LgBx4\\",\\"trafficSourceActivityId\\":\\"\\",\\"sec_source\\":\\"rhhj_dd\\",\\"isOnlyShowShopCart\\":\\"false\\",\\"mrn_component\\":\\"GroupOrderSubmit\\",\\"isDealJudge\\":\\"\\",\\"_referer\\":\\"food-poi\\",\\"flexibleJSON\\":\\"{\\\\\\"assignProm\\\\\\":[]}\\",\\"mrn_hideNextNavBar\\":\\"true\\",\\"hideLoading\\":\\"true\\",\\"groupBuyMopScene\\":\\"1\\",\\"hasKNBParams\\":\\"1\\",\\"venueId\\":\\"\\",\\"mlive_ext\\":\\"\\",\\"buyPoiIdEncrypt\\":\\"qB4r17707da606bc98ea64a037925971660ee8e63d7690a06106e1ce2a76ee607d88922f49ead8b8b2b7712a292610e43d2bac167cdcda7719f50f20vxu5\\",\\"source\\":\\"\\",\\"mrn_adjustParentFrame\\":\\"true\\",\\"productType\\":\\"\\",\\"dealId\\":\\"1635198936\\",\\"lng\\":\\"121.52897062950872\\",\\"halfScreenSubmitHeight\\":\\"0.85\\",\\"payPrice\\":\\"30.9\\",\\"showPrice\\":\\"30.9\\",\\"shelfFusion\\":\\"true\\",\\"lat\\":\\"31.273660438522672\\",\\"dd_source\\":\\"\\",\\"mrn_hideloading\\":\\"true\\",\\"govPromotion\\":\\"\\",\\"isTransparent\\":\\"true\\",\\"buyPoiId\\":\\"1851844943\\",\\"mrn_min_version\\":\\"2.115.0\\",\\"campaignId\\":\\"\\"}",
        "bizExtend": {},
        "userAgreementParam": {
            "agreementInfoList": []
        },
        "pageSceneParam": {
            "pageScene": 0,
            "nextPageScene": 0,
            "promotionPosition": "2109",
            "inflatePosition": "2140",
            "pageTraceInfo": [
                "2026-04-24 17:24:33 doBizPreview   -   -1730337476336438326"
            ],
            "submitBtnStatus": 0,
            "openSelectCouponPageFlag": false,
            "giftIntention": 0,
            "pageSourceId": 0
        },
        "createPriceParam": {},
        "transferDataParam": {
            "transferData": {
                "quantity": "1"
            }
        },
        "operateTypeParam": {
            "operateType": 0
        },
        "cartParam": {
            "promoParamMap": {}
        },
        "diff": false
    },
    "bizRes": {
        "code": 0,
        "message": "成功",
        "userMessage": "成功",
        "data": {
            "abTestVOList": [
                {
                    "key": "ab_group_QDJBH",
                    "douHuTestConfigVOList": [],
                    "horizonTestConfigVOList": [
                        {
                            "expKey": "ab_group_QDJBH",
                            "expResult": true
                        }
                    ],
                    "arenaTestConfigVOList": []
                }
            ],
            "bizResultCode": 0,
            "pageSceneParamVO": {
                "pageScene": 5,
                "nextPageScene": 0,
                "promotionPosition": "2109",
                "pageTraceInfo": [
                    "2026-04-24 17:24:33 doBizPreview   -   -1730337476336438326"
                ],
                "tabInfoVO": [
                    {
                        "pageScene": 5,
                        "tabTitle": "秒提·到店取",
                        "tabTag": "3",
                        "tabStyle": 0
                    },
                    {
                        "pageScene": 1,
                        "tabTitle": "买团购",
                        "tabTag": "3",
                        "tabStyle": 0
                    }
                ],
                "submitBtnStatus": 0,
                "multiTabScene": 1,
                "switchTabType": 1,
                "backPrePageType": 1,
                "openSelectCouponPageFlag": false,
                "giftIntention": 0,
                "pageSourceId": 0
            },
            "preOrderExtParams": "",
            "afterPayInfoVO": {
                "afterPayList": []
            },
            "mopPreOrderVO": {
                "mopShopInfoVO": {
                    "shopId": "1851844943",
                    "shopIcon": "<https://p0.meituan.net/40.40/travelcube/7b5cf1381d1f3c7e1d0896a84dcc56c627952.jpg>",
                    "shopName": "瑞幸咖啡（互联宝地二期店）",
                    "shopAddress": "杨浦区黄兴路221号互联宝地二期负1层B1-68",
                    "chooseShopUrl": "imeituan://www.meituan.com/mrn?mrn_biz=meishi&mrn_entry=ka-mop-poi-select&mrn_component=kaMopPoiSelect&dishSource=10&shopId=1851844943&dealId=1635198936&brandId=288&jumpToShopSelectPageOnLoad=true&pageSource=instant-order-page",
                    "distance": 228,
                    "distanceDesc": "228m",
                    "brandId": "288",
                    "topTipList": [
                        {
                            "content": "附近有多家门店，请确认是否在本店取餐",
                            "type": 0
                        }
                    ],
                    "bottomTipList": [],
                    "topTipRichTextList": [
                        {
                            "content": "<span style='color: #888888;'>距您228m，杨浦区黄兴路221号互联宝地二期负1层B1-68</span>",
                            "type": 0
                        },
                        {
                            "content": "<span style='color: #888888;'>附近有<span style='color: #FF4B10;'>多家门店</span>，请确认取餐门店</span>",
                            "type": 0
                        }
                    ],
                    "tipList": []
                },
                "mopBrandInfoVO": {
                    "brandId": "288",
                    "mopBrandType": 20
                },
                "mopDealMappingInfoVO": {
                    "mopDealMappingProductInfoVO": {
                        "dealId": 1635198936,
                        "dealIdStr": "1635198936",
                        "dealTag": 1,
                        "dealName": "【限量周边】联名光栅卡挂件双杯套餐",
                        "mappingId": "2864067541",
                        "dealMappingType": 30,
                        "mopComboDishDataVO": {
                            "comboProductId": "2312258382",
                            "comboSkuId": "2864067541",
                            "productType": 40,
                            "comboName": "【限量周边】联名光栅卡挂件双杯套餐",
                            "minPrice": "5200",
                            "directAdd": false,
                            "media": {
                                "type": 60,
                                "image": "<https://img.meituan.net/shopdirectconnectpic/abbbfba1279b01072e99fbb49537d64b.jpg>",
                                "backgroundImage": "<http://p0.meituan.net/biztone/eebace0e4375a157dfbf6d285d04e56c4671.png@252w_252h_1e_1c>",
                                "imageList": [
                                    "<https://img.meituan.net/shopdirectconnectpic/582a75d2de7f0b9bfc5a7d54725f4a2a.jpg>"
                                ]
                            },
                            "soldOut": false,
                            "stockStatus": 2,
                            "stock": -1,
                            "comboDishGroupList": [
                                {
                                    "comboGroupName": "饮品",
                                    "comboGroupId": "饮品-0",
                                    "comboDishItemList": [
                                        {
                                            "spuId": "840935279",
                                            "spuName": "生椰拿铁",
                                            "skuIdList": [
                                                "2873171508",
                                                "2873171507",
                                                "2873171509"
                                            ],
                                            "rank": 1,
                                            "media": {
                                                "type": 20,
                                                "image": "<https://img.meituan.net/shopdirectconnectpic/3575dbfa0a59899724b5d906954873e7.jpg>",
                                                "backgroundImage": "<http://p0.meituan.net/biztone/eebace0e4375a157dfbf6d285d04e56c4671.png@252w_252h_1e_1c>",
                                                "imageList": [
                                                    "<https://img.meituan.net/shopdirectconnectpic/bf2e8038eb58a9796134ed2a21070709.jpg>"
                                                ]
                                            },
                                            "soldOut": false,
                                            "stockStatus": 2,
                                            "spuStock": -1,
                                            "currentPrice": "0",
                                            "canCustomization": true,
                                            "defaultChooseNum": 0,
                                            "defaultChooseSku": {
                                                "skuId": "2873171508",
                                                "premiumList": [
                                                    {
                                                        "premiumId": "2540459141",
                                                        "selectNum": 1
                                                    },
                                                    {
                                                        "premiumId": "2540423644",
                                                        "selectNum": 1
                                                    },
                                                    {
                                                        "premiumId": "2540353556",
                                                        "selectNum": 1
                                                    },
                                                    {
                                                        "premiumId": "2540340500",
                                                        "selectNum": 1
                                                    }
                                                ]
                                            },
                                            "needQi": true
                                        },
                                        {
                                            "spuId": "2229378235",
                                            "spuName": "小黄油拿铁",
                                            "skuIdList": [
                                                "2873141811",
                                                "2873141813",
                                                "2873141812"
                                            ],
                                            "rank": 2,
                                            "media": {
                                                "type": 20,
                                                "image": "<https://img.meituan.net/shopdirectconnectpic/260e5f3d8a4a89e9869cbd8d9527d63f.jpg>",
                                                "backgroundImage": "<http://p0.meituan.net/biztone/eebace0e4375a157dfbf6d285d04e56c4671.png@252w_252h_1e_1c>",
                                                "imageList": [
                                                    "<https://img.meituan.net/shopdirectconnectpic/7a7ae382aa8ccb310ac3c520ab8c0770.jpg>"
                                                ]
                                            },
                                            "soldOut": false,
                                            "stockStatus": 2,
                                            "spuStock": -1,
                                            "currentPrice": "0",
                                            "canCustomization": true,
                                            "defaultChooseNum": 0,
                                            "defaultChooseSku": {
                                                "skuId": "2873141811",
                                                "premiumList": [
                                                    {
                                                        "premiumId": "2540444295",
                                                        "selectNum": 1
                                                    },
                                                    {
                                                        "premiumId": "2540330704",
                                                        "selectNum": 1
                                                    },
                                                    {
                                                        "premiumId": "2540301874",
                                                        "selectNum": 1
                                                    },
                                                    {
                                                        "premiumId": "2540280964",
                                                        "selectNum": 1
                                                    }
                                                ]
                                            },
                                            "needQi": true
                                        },
                                        {
                                            "spuId": "2290264283",
                                            "spuName": "苦瓜轻体果蔬茶",
                                            "skuIdList": [
                                                "2878647420",
                                                "2878647421"
                                            ],
                                            "rank": 3,
                                            "media": {
                                                "type": 20,
                                                "image": "<https://img.meituan.net/shopdirectconnectpic/1f1bc1a6bf89a59067b0d6b8928d33fa.jpg>",
                                                "backgroundImage": "<http://p0.meituan.net/biztone/eebace0e4375a157dfbf6d285d04e56c4671.png@252w_252h_1e_1c>",
                                                "imageList": [
                                                    "<https://img.meituan.net/shopdirectconnectpic/8e3a8ae3186bcd9d1454795ac047de81.jpg>"
                                                ]
                                            },
                                            "soldOut": false,
                                            "stockStatus": 2,
                                            "spuStock": -1,
                                            "currentPrice": "0",
                                            "canCustomization": true,
                                            "defaultChooseNum": 0,
                                            "defaultChooseSku": {
                                                "skuId": "2878647420",
                                                "premiumList": [
                                                    {
                                                        "premiumId": "2559186640",
                                                        "selectNum": 1
                                                    },
                                                    {
                                                        "premiumId": "2566595052",
                                                        "selectNum": 1
                                                    },
                                                    {
                                                        "premiumId": "2559269700",
                                                        "selectNum": 1
                                                    }
                                                ]
                                            },
                                            "needQi": false
                                        },
                                        {
                                            "spuId": "2304702978",
                                            "spuName": "冰吸生椰拿铁（首创）",
                                            "skuIdList": [
                                                "2878676656",
                                                "2878676655"
                                            ],
                                            "rank": 4,
                                            "media": {
                                                "type": 20,
                                                "image": "<https://img.meituan.net/shopdirectconnectpic/58a3183d01da56707b3652d362209189.jpg>",
                                                "backgroundImage": "<http://p0.meituan.net/biztone/eebace0e4375a157dfbf6d285d04e56c4671.png@252w_252h_1e_1c>",
                                                "imageList": [
                                                    "<https://img.meituan.net/shopdirectconnectpic/a99caf2fe40a179324b603b2ad14c607.jpg>"
                                                ]
                                            },
                                            "soldOut": false,
                                            "stockStatus": 2,
                                            "spuStock": -1,
                                            "currentPrice": "0",
                                            "canCustomization": true,
                                            "defaultChooseNum": 0,
                                            "defaultChooseSku": {
                                                "skuId": "2878676656",
                                                "premiumList": [
                                                    {
                                                        "premiumId": "2559347768",
                                                        "selectNum": 1
                                                    },
                                                    {
                                                        "premiumId": "2559404566",
                                                        "selectNum": 1
                                                    },
                                                    {
                                                        "premiumId": "2559402655",
                                                        "selectNum": 1
                                                    },
                                                    {
                                                        "premiumId": "2559351882",
                                                        "selectNum": 1
                                                    }
                                                ]
                                            },
                                            "needQi": true
                                        },
                                        {
                                            "spuId": "2316930928",
                                            "spuName": "陨石拿铁",
                                            "skuIdList": [
                                                "2878658750",
                                                "2878658749"
                                            ],
                                            "rank": 5,
                                            "media": {
                                                "type": 20,
                                                "image": "<https://img.meituan.net/shopdirectconnectpic/c619515c3563ee05a7ae72138b28ba62.jpg>",
                                                "backgroundImage": "<http://p0.meituan.net/biztone/eebace0e4375a157dfbf6d285d04e56c4671.png@252w_252h_1e_1c>",
                                                "imageList": [
                                                    "<https://img.meituan.net/shopdirectconnectpic/256630f40ae771533364d5dbfce38fa4.jpg>"
                                                ]
                                            },
                                            "soldOut": false,
                                            "stockStatus": 2,
                                            "spuStock": -1,
                                            "currentPrice": "0",
                                            "canCustomization": true,
                                            "defaultChooseNum": 0,
                                            "defaultChooseSku": {
                                                "skuId": "2878658750",
                                                "premiumList": [
                                                    {
                                                        "premiumId": "2559210984",
                                                        "selectNum": 1
                                                    },
                                                    {
                                                        "premiumId": "2559242608",
                                                        "selectNum": 1
                                                    },
                                                    {
                                                        "premiumId": "2559333065",
                                                        "selectNum": 1
                                                    },
                                                    {
                                                        "premiumId": "2559376102",
                                                        "selectNum": 1
                                                    }
                                                ]
                                            },
                                            "needQi": true
                                        },
                                        {
                                            "spuId": "2317735733",
                                            "spuName": "轻咖 柠檬茶（超大杯）",
                                            "skuIdList": [
                                                "2880849817"
                                            ],
                                            "rank": 6,
                                            "media": {
                                                "type": 20,
                                                "image": "<https://img.meituan.net/shopdirectconnectpic/ee58ca72a73321f7cdfeeac0cc74b10b.jpg>",
                                                "backgroundImage": "<http://p0.meituan.net/biztone/eebace0e4375a157dfbf6d285d04e56c4671.png@252w_252h_1e_1c>",
                                                "imageList": [
                                                    "<https://img.meituan.net/shopdirectconnectpic/700536dfbd626c87485aabd497507030.jpg>"
                                                ]
                                            },
                                            "soldOut": false,
                                            "stockStatus": 2,
                                            "spuStock": -1,
                                            "currentPrice": "0",
                                            "canCustomization": true,
                                            "defaultChooseNum": 0,
                                            "defaultChooseSku": {
                                                "skuId": "2880849817",
                                                "premiumList": [
                                                    {
                                                        "premiumId": "2565180779",
                                                        "selectNum": 1
                                                    },
                                                    {
                                                        "premiumId": "2565322176",
                                                        "selectNum": 1
                                                    },
                                                    {
                                                        "premiumId": "2565364149",
                                                        "selectNum": 1
                                                    },
                                                    {
                                                        "premiumId": "2565266242",
                                                        "selectNum": 1
                                                    }
                                                ]
                                            },
                                            "needQi": false
                                        },
                                        {
                                            "spuId": "841630645",
                                            "spuName": "橙C美式",
                                            "skuIdList": [
                                                "2873155689",
                                                "2873155688"
                                            ],
                                            "rank": 7,
                                            "media": {
                                                "type": 20,
                                                "image": "<https://img.meituan.net/shopdirectconnectpic/853f61fcf4ceeee4da067ad73fdc5ef7.jpg>",
                                                "backgroundImage": "<http://p0.meituan.net/biztone/eebace0e4375a157dfbf6d285d04e56c4671.png@252w_252h_1e_1c>",
                                                "imageList": [
                                                    "<https://img.meituan.net/shopdirectconnectpic/0a656446e8100cbe0d183dd486ea9a8e.jpg>"
                                                ]
                                            },
                                            "soldOut": false,
                                            "stockStatus": 2,
                                            "spuStock": -1,
                                            "currentPrice": "0",
                                            "canCustomization": true,
                                            "defaultChooseNum": 0,
                                            "defaultChooseSku": {
                                                "skuId": "2873155689",
                                                "premiumList": [
                                                    {
                                                        "premiumId": "2540410001",
                                                        "selectNum": 1
                                                    },
                                                    {
                                                        "premiumId": "2540338659",
                                                        "selectNum": 1
                                                    },
                                                    {
                                                        "premiumId": "2540338660",
                                                        "selectNum": 1
                                                    },
                                                    {
                                                        "premiumId": "2540397275",
                                                        "selectNum": 1
                                                    },
                                                    {
                                                        "premiumId": "2540353638",
                                                        "selectNum": 1
                                                    }
                                                ]
                                            },
                                            "needQi": true
                                        }
                                    ],
                                    "rank": 0,
                                    "fixed": false,
                                    "minChoiceNum": 2,
                                    "maxChoiceNum": 2,
                                    "repeatChooseNum": 2,
                                    "showPrice": true
                                },
                                {
                                    "comboGroupName": "周边",
                                    "comboGroupId": "周边-1",
                                    "comboDishItemList": [
                                        {
                                            "spuId": "2317597872",
                                            "spuName": "光栅卡挂件·自嘲熊和朋友们系列",
                                            "skuIdList": [
                                                "2880906263"
                                            ],
                                            "rank": 1,
                                            "media": {
                                                "type": 20,
                                                "image": "<https://img.meituan.net/shopdirectconnectpic/fd46d472ca2919616311af2fe0be12ea.jpg>",
                                                "backgroundImage": "<http://p0.meituan.net/biztone/eebace0e4375a157dfbf6d285d04e56c4671.png@252w_252h_1e_1c>",
                                                "imageList": [
                                                    "<https://img.meituan.net/shopdirectconnectpic/44fe3a42b4ce7511a046b52f1d992a06.jpg>"
                                                ]
                                            },
                                            "soldOut": false,
                                            "stockStatus": 1,
                                            "spuStock": 5,
                                            "currentPrice": "0",
                                            "canCustomization": false,
                                            "defaultChooseNum": 0,
                                            "defaultChooseSku": {
                                                "skuId": "2880906263",
                                                "premiumList": []
                                            },
                                            "needQi": false
                                        }
                                    ],
                                    "rank": 1,
                                    "fixed": false,
                                    "minChoiceNum": 1,
                                    "maxChoiceNum": 1,
                                    "repeatChooseNum": 1,
                                    "showPrice": true
                                }
                            ],
                            "extendInfoMap": {
                                "COMBO_ADD_PRICE_WITH_RAW": "1"
                            },
                            "needQi": false
                        }
                    },
                    "isSupport": true,
                    "dealUpperLimit": 100,
                    "skuUpperLimit": 15
                },
                "mopProductPriceVO": {
                    "currentPrice": "3090",
                    "mopCurrentPrice": "null",
                    "dealCurrentPrice": "3090",
                    "discountPrice": "4510",
                    "totalPrice": "7600",
                    "selectNum": 1,
                    "dealTotalPrice": "7600",
                    "dealDiscountPrice": "4510",
                    "needQi": false
                },
                "currentPage": 10,
                "usePromotionDetails": [
                    {
                        "promoId": "685890111740298235",
                        "promoType": 6,
                        "totalDiscount": 300,
                        "activityProductId": 11,
                        "title": "神券-吃喝玩乐神券"
                    }
                ]
            },
            "transferDataVO": {
                "transferData": {
                    "quantity": "1"
                }
            },
            "giftInfoVO": {
                "canGive": false
            }
        },
        "success": true,
        "fail": false
    }
}
```

### 结论

可以看出

dealMappingType 标志位 30表示是联名套餐 20是正常？

> 还是说 productType 才是标志位
> 

data.nodeDataMap.MopContainer.p.onlineOrderPropsVo.mopDealMappingInfoVO.mopDealMappingProductInfoVO.mopComboDishDataVO.comboDishGroupList 中存储了联名套餐的信息

## 打通过程

### 首先了解如何获取商品信息

```
// 代码块
现在 `mop-order` 获取商品信息分两层：

1. **门店货架商品列表**
   Skill 先确定 `poiId`，然后执行 `food-mop-order poi <poiId>`。CLI 会带登录 token 和设备信息，请求：
   `GET <https://apimeishi.meituan.com/meishi/poi/v1/poi/combinedinfos/:poiId`>

   解析位置在 [api/poi.ts](/Users/ceilf6/Desktop/ka-skills/cli/mop/mop-order/src/api/poi.ts:31)。它从 `data.dealListV4.productInfo` 里取：
   `products`、`filters.filterItems`、秒提支持状态、营业状态、轮播等待文案等，再归一化成 `id/title/price/originalPrice/soldNum/stock/imageUrl/tags`。输出命令在 [command/poi.ts](/Users/ceilf6/Desktop/ka-skills/cli/mop/mop-order/src/command/poi.ts:47)。

2. **单个商品/团购的规格详情**
   选中 `dealId` 后执行 `food-mop-order deal <poiId> <dealId>`。CLI 请求：
   `POST <https://rpc.meituan.com/grouptrade/precreate/preview`>

   解析位置在 [api/deal.ts](/Users/ceilf6/Desktop/ka-skills/cli/mop/mop-order/src/api/deal.ts:32)。它从 `nodeDataMap.MopContainer.p.onlineOrderPropsVo` 里取门店、商品、价格和 SKU 规格，生成 `dealDetail.productGroups.products[].skuList/attrGroups`。默认输出会把售卖属性旁边补上 `[skuId:xxx]`，方便后续下单读取，见 [command/deal.ts](/Users/ceilf6/Desktop/ka-skills/cli/mop/mop-order/src/command/deal.ts:96)。

补充一个关键点：Skill 文档里还规定，如果用户直接说商品名，会先从货架里找 `N选1/任选N` 团购，再最多展开 3 个 `deal --json` 去子商品列表里模糊匹配；找不到才回落到货架单品匹配，见 [SKILL.md](/Users/ceilf6/Desktop/ka-skills/skills/user-mop-order/SKILL.md:108)。

所以它不是靠本地缓存拿实时商品。历史记录只辅助选择上次门店/商品名，真正商品列表和规格都来自线上接口实时返回。
```

### PROMPT

```
// 代码块
由于联名套餐商品和其他商品返回的数据格式不一致，所以现在点餐联名套餐无法打通
/Users/ceilf6/Desktop/ka-skills-mop-order-response 中存储了同一个接口 /grouptrade/precreate/preview 联名套餐的返回 combo.json 和除联名套餐外的其他商品返回 normal.json ，我分析了一下好像
1. dealMappingType 标志位 30表示是联名套餐
2. comboDishGroupList 中存储了联名套餐的信息
你需要读取、校验上面信息，优化 mop-order 这个skill
```

### 变更

```
// 代码块
已继续完成并验证。

mop-order 获取商品信息的主链路是 `/grouptrade/precreate/preview`，解析 `mopDealMappingInfoVO.mopDealMappingProductInfoVO`。这次校验你的判断基本正确：`dealMappingType=30` 表示联名/直连套餐；不过 `comboDishGroupList` 不是直接挂在 mapping 根上，而是在 `mopComboDishDataVO.comboDishGroupList` 下。

我已优化：

- [deal.ts](/Users/ceilf6/Desktop/ka-skills/cli/mop/mop-order/src/api/deal.ts)：新增解析 `mopComboDishDataVO.comboDishGroupList`
- [deal.ts](/Users/ceilf6/Desktop/ka-skills/cli/mop/mop-order/src/command/deal.ts)：`food-mop-order deal` 可展示联名套餐分组、`spuId`、默认 `skuId`
- [order.ts](/Users/ceilf6/Desktop/ka-skills/cli/mop/mop-order/src/command/order.ts)：支持 `dealMappingType=30`，新增 `--combo-spu` / `--combo-sku`，构造 `mopComboDishItem`
- [submit.ts](/Users/ceilf6/Desktop/ka-skills/cli/mop/mop-order/src/command/submit.ts)：全流程提交支持 type 30
- [order api](/Users/ceilf6/Desktop/ka-skills/cli/mop/mop-order/src/api/order.ts)：兼容解析 `mopComboDishVO`
- [SKILL.md](/Users/ceilf6/Desktop/ka-skills/skills/user-mop-order/SKILL.md) 和 CLI 文档已更新联名套餐使用方式

验证结果：

- `pnpm --dir cli/mop/mop-order run typecheck` 通过
- `pnpm --dir cli/mop/mop-order run build` 通过
- 隔离 HOME 后跑 `test:cases`：2 通过，0 失败，2 跳过
- 用你给的 `combo.json` 验证：`dealMappingType=30`，解析到 2 个联名套餐分组：饮品、周边
- 用 `normal.json` 验证：`dealMappingType=20`，仍走原普通套餐 productGroups
- mock 预提单请求已确认包含：`dealMappingType: 30`、`mopComboDishItem`、`comboProductId`、`comboSkuId`、`mopComboSkuItemList`

注意点：当前 preview 接口对 type 30 只返回子商品和默认 SKU/premium，没有完整温度、糖度等可读客制化信息，所以 skill 里也明确为联名套餐暂按默认客制化下单。
```

### CR

### 总体结论

这次改动**方向正确**：已经用 `dealMappingType === 30` 作为联名/直连套餐标识，并且把联名套餐关键数据从 `mopComboDishDataVO.comboDishGroupList` 解析出来，同时在 `order/submit` 侧补了 `--combo-spu/--combo-sku` 的入参通路，文档与冒烟用例也同步更新了。整体上，**普通商品（type=10/20）的链路看起来没有被强行改写**，是比较“外科手术式”的接入。

下面是我按风险等级给的 Code Review。

---

### ✅ 做得好的点（建议保留）

- **联名套餐识别信号清晰**：用 `dealMappingType=30` 分支处理，且 `comboDishGroupList` 确实存在于 `combo.json` 中（而 `normal.json` 为 type=20），与背景判断一致。
- **解析层兼容性增强**：`parseOrderUpdateResponse` 同时兼容 `item.mopComboVO` 和 `item.mopComboDishVO`，避免仅联名套餐走空列表。

```
// 代码块
      result.product = purchaseItems.map((item: any) => {
        const combo = item.mopComboVO;
        const dishCombo = item.mopComboDishVO;
        const comboSkus = combo?.mopComboSkuVOList ?? dishCombo?.mopComboSkuVOList ?? [];
        const skus = comboSkus.map((sku: any) => ({
          // ...
          itemKey: sku.itemKey,
          selectNum: sku.comboSkuNum ?? sku.selectNum ?? 1,
          premiums: (sku.mopPremiumVOList ?? sku.mopPremiumItemVOList ?? []).map((premium: any) => ({
            premiumId: premium.premiumId,
            selectNum: premium.premiumNum ?? premium.selectNum ?? 1,
            payPrice: premium.payPrice,
          })),
        }));
        return {
          purchaseItemType: item.purchaseItemType,
          dealMappingType: item.dealMappingType,
          dealId: item.dealId,
          dealIdStr: item.dealIdStr ?? String(item.dealId),
          // ...
          comboDishProductId: dishCombo?.comboProductId,
          comboDishSkuId: dishCombo?.comboSkuId,
          comboDishName: dishCombo?.comboName,
          skus,
        };
      });
```

- **CLI 文档/skill 文档/冒烟用例闭环**：`skills/user-mop-order/SKILL.md` 已明确“联名套餐客制化按默认值，不承诺可改”，并新增 Case 8 覆盖联名套餐下单链路。

---

### 🔴 高风险问题（建议上线前必须确认/修正）

- `*userSelectedDealItem 里存在明显的占位/脏数据**`：`toastTip: 'undefined还需选0份'` 这种字符串非常像临时占位，可能会被服务端校验/风控/埋点链路依赖，导致不可预期的拒单或埋点污染。

```
// 代码块
    firstInvalidItem: {
      anchorKey: '',
      toastTip: 'undefined还需选0份',
    },
    mopDishComboItem: {
      itemKey: combo?.itemKey ?? '',
      selectAll: true,
      noOneSelected: currSelectedList.length === 0,
      comboProductId: combo?.comboProductId ?? '',
      comboSkuId: combo?.comboSkuId ?? '',
      dealMappingType: 30,
      currSelectedList,
      mopComboSkuItemList: unmergedComboSkuItems,
    },
```

- **联名套餐 itemKey 构造存在碰撞/不可控长度风险**：`itemKeySuffix = selected.map(...).join('')` 没有分隔符，理论上可能产生拼接碰撞；同时 itemKey 变长会不会触发后端长度限制也未知。这个值又被用于 `mopDealPurchaseItemList[0].itemKey`，如果后端强校验（或用于缓存 key / 埋点 key），风险较大。

---

### 🟠 中风险问题（建议尽快改，但可灰度验证）

- `*parseComboDishData 里“造”了 SKU 的 skuName/price/addPrice**`：现在把 `currentPrice` 同时当作 `originalPrice/addPrice`，并用 `SKU ${skuId}` 伪造名称。只要这些字段不参与计算还好，但它会误导使用者（尤其是 Agent/人读输出）并可能被后续逻辑误用。
    - 更稳妥的做法：**只保留真实存在且你确实需要的字段**（`spuId/spuName/skuIdList/defaultChooseSku/premiumList/soldOut/stock...`），不要伪造价格与名称。
- `*--combo-spu/--combo-sku 复用了 collectAttrs**`：实现上能收集多值，但语义上 `collectAttrs` 是为 `-attr group:value` 设计的，未来维护容易混淆（可读性问题）。

---

### 🟡 低风险/体验问题（不影响正确性，但建议优化）

- `deal` 命令遇到 type=30 就 `return`，不会再打印普通规格组；这符合当前“联名套餐只返回默认 premium”事实，但建议在输出里再强调一次“当前仅能选子商品，客制化按默认值”，你已经打印了提示，这点不错。
- `submit`/`order` 的展示逻辑对 type=30 增加了“子商品列表”输出，体验提升明显；不过建议统一展示字段（例如子商品的 `spuId/skuId`）以便用户复述选择。

---

### 关键路径覆盖检查（我认为已满足）

- **识别联名套餐**：`dealMappingType === 30` ✅
- **读取联名套餐信息**：从 `mopComboDishDataVO.comboDishGroupList` ✅（与 `combo.json` 一致）
- **构造联名套餐 purchaseItem**：`mopDealPurchaseItemList[0].mopComboDishItem.mopComboSkuItemList` ✅（代码路径已打通）
- **文档/用例更新**：README、Skill、cli-reference、smoke ✅

---

### 我建议你上线前至少补的验证点（不需要大改，但要验证）

- 用真实/录制响应跑一次全链路（`deal -> order -> submit`）确保：
    - `buildFrontParamMap(...).userSelectedDealItem` 的结构/字段名（`mopDishComboItem` vs `mopComboDishItem`）**确实是后端期望的**
    - 上面提到的 `toastTip`、`itemKey` 不会触发后端校验

如果你希望我继续做“更深一层”的 Review（把 `submit.ts` 的 type=30 构造、以及 `deal.ts parseComboDishData` 的字段取值逐项对照抓包/样例），我可以再把这两块的具体字段对照列出来并标出“可信/不可信/应删除伪造字段”的清单。

### 继续循环

```
// 代码块
# mop-order 联名套餐 CR 优化计划

## Summary
基于 CR 和本地对照，保留当前 `dealMappingType=30` 接入方向，只做外科式加固：去掉脏占位字段、停止伪造 SKU 数据、提升参数收集可读性，并保护联名套餐 `itemKey` 的前端兼容形态。

## Key Changes
- `userSelectedDealItem.firstInvalidItem`：type=30 已经由 CLI 补齐并校验选择，改为 `null`，不再输出 `toastTip: "undefined还需选0份"`。
- `itemKey`：不改协议形态。已对照 `ka-mop-max-duo`，前端也是把子商品 key 直接串接；实现上提取成明确 helper，并加验证，避免未来误改。
- `parseComboDishData`：删除伪造的 `skuList.skuName/currentPrice/originalPrice/addPrice/saleAttrs/customRules` 和空 `attrGroups`；只保留接口真实返回且下单需要的字段，如 `spuId/spuName/skuIdList/defaultChooseSku/defaultChooseNum/soldOut/stock/currentPrice/imageUrl/rank`。
- `--combo-spu/--combo-sku`：新增语义化收集函数，例如 `collectValues`，不再复用 `collectAttrs`；`--attr` 仍保留原函数。
- type=30 文本输出：子商品列表补充 `[spuId:xxx] [skuId:xxx]`，便于用户核对和复述。

## Public Interface Notes
- CLI flags 不变：仍使用 `--combo-spu` / `--combo-sku`。
- `deal --json` 中 type=30 的 `comboDishGroups.products[]` 会移除之前人为构造的伪 SKU 展示字段；保留真实选择和下单所需字段。
- `order/submit` 的普通 type=10/20 链路不改。

## Test Plan
- 跑 `pnpm --dir cli/mop/mop-order run typecheck`。
- 跑 `pnpm --dir cli/mop/mop-order run build`。
- 用隔离 HOME 跑 `TEST_AUTH_STATE=logged_out pnpm --dir cli/mop/mop-order run test:cases`。
- 用 `combo.json` 验证：
  - `deal --json` 仍解析出 `dealMappingType=30` 和 2 个 `comboDishGroups`。
  - `order --combo-spu ... --verbose` 请求仍包含 `mopComboDishItem`、`mopComboSkuItemList`、`comboProductId`、`comboSkuId`。
  - verbose 输出中不再出现 `undefined还需选0份`。
- 用 `normal.json` 验证 type=20 仍解析为 `productGroups`，`comboDishGroups` 为空。

## Assumptions
- 不做真实 `submit`，避免未确认下单；只做 mock/verbose 级别验证。
- `itemKey` 以 `ka-mop-max-duo` 现有前端实现为准，优先兼容后端/前端已有 wire shape，不为了理论碰撞风险改协议。
```

```
// 代码块
已按 CR 优化计划实现，保持 type=30 主链路不变，只做加固。

主要改动：

- [order.ts](/Users/ceilf6/Desktop/ka-skills/cli/mop/mop-order/src/command/order.ts)：type=30 的 `userSelectedDealItem.firstInvalidItem` 改为 `null`，移除 `undefined还需选0份`；抽出联名套餐 `itemKey` helper，并保留与 `ka-mop-max-duo` 一致的“子 key 直接串接”形态；`--combo-spu/--combo-sku` 改用 `collectValues`
- [deal.ts](/Users/ceilf6/Desktop/ka-skills/cli/mop/mop-order/src/api/deal.ts)：type=30 子商品不再伪造 `skuList`、`skuName`、价格、`attrGroups`
- [submit.ts](/Users/ceilf6/Desktop/ka-skills/cli/mop/mop-order/src/command/submit.ts)：同步 `collectValues`，type=30 展示子商品时补充 `[spuId]` / `[skuId]`
- [CHANGELOG.md](/Users/ceilf6/Desktop/ka-skills/cli/mop/mop-order/CHANGELOG.md)：补充 CR 加固记录

验证已跑：

- `pnpm --dir cli/mop/mop-order run typecheck` 通过
- `pnpm --dir cli/mop/mop-order run build` 通过
- 隔离 HOME 跑 `TEST_AUTH_STATE=logged_out pnpm --dir cli/mop/mop-order run test:cases`：2 通过，0 失败，2 跳过
- `combo.json` 回归：`dealMappingType=30`，2 个 `comboDishGroups`，子商品已无 `skuList/attrGroups`
- `normal.json` 回归：`dealMappingType=20`，普通 `productGroups` 不受影响
- type=30 verbose 构单仍包含 `mopComboDishItem`、`mopComboSkuItemList`、`comboProductId`、`comboSkuId`，且 `undefined还需选0份` 已不存在

没有跑真实 `submit`，只做了 mock/verbose 验证，避免实际下单。
```

### Agent测试阻塞

```
// 代码块
所有联名套餐（dealMappingType=30）的 productGroups 都是空的，CLI 暂时无法获取子商品选择。
抱歉，目前所有联名套餐（包括【咸鱼抽拉挂件·蛋仔派对】双杯套）的子商品规格无法通过 CLI 获取，下单会报错「无法从 deal preview 中提取商品信息」。
```

但是联名商品的 productGroups 为空是正常的

所以需要纠正其捕获商品信息的路径

```
// 代码块
已修正。这里的关键点是：你说得对，`dealMappingType=30` 的 `productGroups=[]` 是正常现象，不能据此判定“CLI 无法获取子商品”。这类联名套餐要读 `mopComboDishDataVO.comboDishGroupList`，CLI 输出里的归一化字段是 `dealDetail.comboDishGroups`。

这次我做了两类修复：

- [deal.ts](/Users/ceilf6/Desktop/ka-skills/cli/mop/mop-order/src/api/deal.ts)：增强 `/grouptrade/precreate/preview` 解析。优先走固定路径，找不到时递归兜底查找 `mopDealMappingProductInfoVO`，避免 MRN 外壳位置变化时误判。
- [SKILL.md](/Users/ceilf6/Desktop/ka-skills/skills/user-mop-order/SKILL.md)、[cli-reference.md](/Users/ceilf6/Desktop/ka-skills/skills/user-mop-order/references/cli-reference.md)、[troubleshooting.md](/Users/ceilf6/Desktop/ka-skills/skills/user-mop-order/references/troubleshooting.md)、[smoke.md](/Users/ceilf6/Desktop/ka-skills/skills/user-mop-order/tests/smoke.md)：明确写死规则：type=30 不看 `productGroups`，必须看 `comboDishGroups`；`productGroups=[]` 不代表不可下单。

我用你给的新 fixture 验证了：

- `combo-【限定周边】联名咸鱼抽拉毛绒双杯套餐.json`
- 解析结果：`dealMappingType=30`、`productGroups=0`、`comboDishGroups=2`，分组为「饮品」「周边」
- `order --combo-spu 840935279 --combo-spu 2304702978 --combo-spu 2331272770 --verbose` 能构出 `mopComboDishItem` / `mopComboSkuItemList`

同时已跑：

- `pnpm --dir cli/mop/mop-order run typecheck` 通过
- `pnpm --dir cli/mop/mop-order run build` 通过
- 隔离 HOME 的 `test:cases`：2 通过，0 失败，2 跳过
- 旧的 `combo.json` / `normal.json` 回归也正常

没有跑真实 `submit`，避免实际下单。
```

根因是因为 CLI 没有同步，对应参数无法录入

### 更新CLI

```
// 代码块
▎ [🟠 阿里味] 你这个质疑是对的。我前面打通的是 workspace 链路，没把“用户实际执行的全局 CLI”闭环，这就是交付漏斗漏了最后一层。现在补上了。

📊 Sprint 交付 · 证据闭环
┌──────────────┬──────────────────────────────┐
│ 根因          │ registry latest 仍是 0.4.4，全局 CLI 旧 │
├──────────────┼──────────────────────────────┤
│ 本机全局 CLI  │ 已安装本地构建版 0.4.5       │
├──────────────┼──────────────────────────────┤
│ 参数探活      │ order/submit 均有 --combo-spu │
├──────────────┼──────────────────────────────┤
│ 咸鱼套餐回归  │ global food-mop-order order 通过 │
└──────────────┴──────────────────────────────┘

我做了这些补救：

- [package.json](/Users/ceilf6/Desktop/ka-skills/cli/mop/mop-order/package.json)：CLI 版本升到 `0.4.5`
- [bin/cli.js](/Users/ceilf6/Desktop/ka-skills/cli/mop/mop-order/bin/cli.js)：补了 `food-mop-order --version`
- [cases.json](/Users/ceilf6/Desktop/ka-skills/cli/mop/mop-order/tests/cases.json)：新增 `order/submit --help` 必须包含 `--combo-spu` 的回归用例
- [SKILL.md](/Users/ceilf6/Desktop/ka-skills/skills/user-mop-order/SKILL.md)：前置检查改成先探活，避免本机 0.4.5 被 registry 旧 `latest` 覆盖降级

验证数据：

- `food-mop-order --version` → `0.4.5`
- `food-mop-order order --help` → 已包含 `--combo-spu` / `--combo-sku`
- `food-mop-order submit --help` → 已包含 `--combo-spu` / `--combo-sku`
- 用全局 `food-mop-order` 跑咸鱼套餐 mock order：`global_combo_order=ok`
- `pnpm --dir cli/mop/mop-order run typecheck` 通过
- `pnpm --dir cli/mop/mop-order run build:clean` 通过
- `test:cases`：4 通过，0 失败，2 跳过

还有一个硬事实：内网 npm registry 现在 `latest` 仍是 `0.4.4`，我这台机器没有 npm 发布登录态，`npm whoami --registry <http://r.npm.sankuai.com`> 返回 `ENEEDAUTH`。所以我已经把本机全局 CLI 修到可用，并把 `0.4.5` 发布包 dry-run 验过；真正推到 registry 需要有发布权限的人登录后执行 publish。
```

### 清理无效复杂逻辑

```
// 代码块
[$pua](/Users/ceilf6/.codex/skills/pua/SKILL.md) [$karpathy-guidelines](/Users/ceilf6/.codex/skills/karpathy-guidelines/SKILL.md) 为什么要针对本地包做一大堆没必要的复杂逻辑？正确的做法不应该是直接发布新版本包吗？
```

不应该用本地包，应该 publish

```
// 代码块
cd /Users/ceilf6/Desktop/ka-skills/cli/mop/mop-order
npm adduser --registry <http://r.npm.sankuai.com>
npm publish --registry <http://r.npm.sankuai.com>
npm view @meishi/food-mop-order version dist-tags --registry <http://r.npm.sankuai.com>
```

但是在 adduser 时错误

于是在学城内搜索 "内网npm发布" 后找到了 [https://km.sankuai.com/collabpage/2757191865](https://km.sankuai.com/collabpage/2757191865) 中描述已经有内置维护包版本的脚本

但是仍然需要打通账号权限，找到文档 [https://km.sankuai.com/collabpage/127620956](https://km.sankuai.com/collabpage/127620956)

SSO登陆后，发布包遇到权限问题，[https://km.sankuai.com/collabpage/127620956#b-de990765825d45f7ab9526151e8d8a75](https://km.sankuai.com/collabpage/127620956#b-de990765825d45f7ab9526151e8d8a75)，让露姐`mnpm owner add wangjinghong02 @meishi/food-mop-order`

### 客制化

```
// 代码块
了解！不过这是联名套餐，当前接口不支持修改温度/糖度等客制化规格，只能使用默认值。
```

需要额外提供接口数据 [https://apimobile.meituan.com/mop/api/menu/productDetailForPoiShelf](https://apimobile.meituan.com/mop/api/menu/productDetailForPoiShelf)

查看了别的 type 商品获取客制化信息都是直接从 grouptrade 接口就可以直接拿到

但是联动套餐不行，所以可能得新增一个接口请求

```
// 代码块
{
  "code": 200,
  "msg": "成功",
  "data": {
    "mopShopInfoVO": {
      "shopId": "1851844943",
      "shopName": "瑞幸咖啡（互联宝地二期店）",
      "shopIcon": "<https://p0.meituan.net/40.40/travelcube/7b5cf1381d1f3c7e1d0896a84dcc56c627952.jpg>",
      "shopAddress": "杨浦区黄兴路221号互联宝地二期负1层B1-68",
      "chooseShopUrl": "imeituan://www.meituan.com/mrn?mrn_biz=meishi&mrn_entry=ka-mop-poi-select&mrn_component=kaMopPoiSelect&dishSource=10&shopId=1851844943&brandId=288&jumpToShopSelectPageOnLoad=true&pageSource=instant-order-page",
      "distance": 239,
      "brandId": "288",
      "prepareTimeRichText": {
        "templateText": "预计准备时间Y-Z分钟",
        "predictMinTime": "6",
        "predictMaxTime": "8",
        "style": {
          "color": "#29CC29"
        }
      },
      "topTipList": [
        {
          "position": "top",
          "content": "附近有多家门店，请确认是否在本店取餐",
          "type": 0
        }
      ],
      "topTipRichTextList": [
        {
          "position": "top",
          "content": "<span style='color: #888888;'>距您239m，杨浦区黄兴路221号互联宝地二期负1层B1-68</span>",
          "type": 0
        },
        {
          "position": "top",
          "content": "<span style='color: #888888;'>附近有<span style='color: #FF4B10;'>多家门店</span>，请确认取餐门店</span>",
          "type": 0
        }
      ]
    },
    "mopBrandInfoVO": {
      "brandId": "288",
      "mopBrandType": 20
    },
    "mopDealMappingInfoVO": {
      "mopDealMappingProductInfoVO": {
        "dealId": "-1",
        "dealName": "冰吸生椰拿铁（首创）",
        "dealMappingType": 10,
        "dealMappingChooseType": 2,
        "mopProductInfoVO": {
          "spuName": "冰吸生椰拿铁（首创）",
          "spuId": "2304702978",
          "isAvailable": true,
          "spuPicAddr": "<https://img.meituan.net/shopdirectconnectpic/58a3183d01da56707b3652d362209189.jpg>",
          "defaultSkuId": "2878676656",
          "mopSkuList": [
            {
              "skuId": "2878676656",
              "spuId": "2304702978",
              "skuName": "大杯",
              "isAvailable": true,
              "currentPrice": "3500",
              "originalPrice": "3500",
              "addPrice": "3500",
              "stockCount": -1,
              "mopSkuSaleAttrList": [
                {
                  "groupCode": "64",
                  "attributeId": "2497190611"
                }
              ],
              "mopCustomRuleList": [
                {
                  "premiumGroupCode": "17",
                  "defaultSelect": true,
                  "mustSelect": true,
                  "maxChoice": 1,
                  "minChoice": 1,
                  "defaultSelectNum": 1,
                  "unitPerStep": 1,
                  "exchange": false,
                  "hide": false,
                  "fold": false,
                  "rank": 1,
                  "ruleType": 10,
                  "multiChoice": false,
                  "groupMultiChoice": false
                },
                {
                  "premiumGroupCode": "50",
                  "defaultSelect": true,
                  "mustSelect": true,
                  "maxChoice": 1,
                  "minChoice": 1,
                  "defaultSelectNum": 1,
                  "unitPerStep": 1,
                  "exchange": false,
                  "hide": false,
                  "fold": false,
                  "rank": 2,
                  "ruleType": 10,
                  "multiChoice": false,
                  "groupMultiChoice": false
                },
                {
                  "premiumGroupCode": "113",
                  "defaultSelect": true,
                  "mustSelect": true,
                  "maxChoice": 1,
                  "minChoice": 1,
                  "defaultSelectNum": 1,
                  "unitPerStep": 1,
                  "exchange": false,
                  "hide": false,
                  "fold": false,
                  "rank": 3,
                  "ruleType": 10,
                  "multiChoice": false,
                  "groupMultiChoice": false
                },
                {
                  "premiumGroupCode": "18",
                  "defaultSelect": true,
                  "mustSelect": true,
                  "maxChoice": 1,
                  "minChoice": 1,
                  "defaultSelectNum": 1,
                  "unitPerStep": 1,
                  "exchange": false,
                  "hide": false,
                  "fold": false,
                  "rank": 4,
                  "ruleType": 10,
                  "multiChoice": false,
                  "groupMultiChoice": false
                },
                {
                  "premiumId": "2559347768",
                  "premiumGroupCode": "17",
                  "defaultSelect": true,
                  "mustSelect": false,
                  "maxChoice": 1,
                  "minChoice": 0,
                  "maxFreeNum": 0,
                  "defaultSelectNum": 1,
                  "unitPerStep": 1,
                  "exchange": false,
                  "hide": false,
                  "rank": 1,
                  "ruleType": 20,
                  "multiChoice": false,
                  "groupMultiChoice": false,
                  "price": "0",
                  "premiumName": "冰"
                },
                {
                  "premiumId": "2559404566",
                  "premiumGroupCode": "50",
                  "defaultSelect": true,
                  "mustSelect": false,
                  "maxChoice": 1,
                  "minChoice": 0,
                  "maxFreeNum": 0,
                  "defaultSelectNum": 1,
                  "unitPerStep": 1,
                  "exchange": false,
                  "hide": false,
                  "rank": 1,
                  "ruleType": 20,
                  "multiChoice": false,
                  "groupMultiChoice": false,
                  "price": "0",
                  "premiumName": "意式拼配"
                },
                {
                  "premiumId": "2559402655",
                  "premiumGroupCode": "113",
                  "defaultSelect": true,
                  "mustSelect": false,
                  "maxChoice": 1,
                  "minChoice": 0,
                  "maxFreeNum": 0,
                  "defaultSelectNum": 1,
                  "unitPerStep": 1,
                  "exchange": false,
                  "hide": false,
                  "rank": 1,
                  "ruleType": 20,
                  "multiChoice": false,
                  "groupMultiChoice": false,
                  "price": "0",
                  "premiumName": "默认浓度"
                },
                {
                  "premiumId": "2559361699",
                  "premiumGroupCode": "18",
                  "defaultSelect": false,
                  "mustSelect": false,
                  "maxChoice": 1,
                  "minChoice": 0,
                  "maxFreeNum": 0,
                  "defaultSelectNum": 1,
                  "unitPerStep": 1,
                  "exchange": false,
                  "hide": false,
                  "rank": 1,
                  "ruleType": 20,
                  "multiChoice": false,
                  "groupMultiChoice": false,
                  "price": "0",
                  "premiumName": "标准甜"
                },
                {
                  "premiumId": "2559380099",
                  "premiumGroupCode": "50",
                  "defaultSelect": false,
                  "mustSelect": false,
                  "maxChoice": 1,
                  "minChoice": 0,
                  "maxFreeNum": 0,
                  "defaultSelectNum": 1,
                  "unitPerStep": 1,
                  "exchange": false,
                  "hide": false,
                  "rank": 2,
                  "ruleType": 20,
                  "multiChoice": false,
                  "groupMultiChoice": false,
                  "price": "0",
                  "premiumName": "深烘拼配"
                },
                {
                  "premiumId": "2559341294",
                  "premiumGroupCode": "113",
                  "defaultSelect": false,
                  "mustSelect": false,
                  "maxChoice": 1,
                  "minChoice": 0,
                  "maxFreeNum": 0,
                  "defaultSelectNum": 1,
                  "unitPerStep": 1,
                  "exchange": false,
                  "hide": false,
                  "rank": 2,
                  "ruleType": 20,
                  "multiChoice": false,
                  "groupMultiChoice": false,
                  "price": "300",
                  "premiumName": "加单份浓缩"
                },
                {
                  "premiumId": "2559306598",
                  "premiumGroupCode": "18",
                  "defaultSelect": false,
                  "mustSelect": false,
                  "maxChoice": 1,
                  "minChoice": 0,
                  "maxFreeNum": 0,
                  "defaultSelectNum": 1,
                  "unitPerStep": 1,
                  "exchange": false,
                  "hide": false,
                  "rank": 2,
                  "ruleType": 20,
                  "multiChoice": false,
                  "groupMultiChoice": false,
                  "price": "0",
                  "premiumName": "少甜"
                },
                {
                  "premiumId": "2559371693",
                  "premiumGroupCode": "50",
                  "defaultSelect": false,
                  "mustSelect": false,
                  "maxChoice": 1,
                  "minChoice": 0,
                  "maxFreeNum": 0,
                  "defaultSelectNum": 1,
                  "unitPerStep": 1,
                  "exchange": false,
                  "hide": false,
                  "rank": 3,
                  "ruleType": 20,
                  "multiChoice": false,
                  "groupMultiChoice": false,
                  "price": "0",
                  "premiumName": "埃塞金烘"
                },
                {
                  "premiumId": "2559346070",
                  "premiumGroupCode": "18",
                  "defaultSelect": false,
                  "mustSelect": false,
                  "maxChoice": 1,
                  "minChoice": 0,
                  "maxFreeNum": 0,
                  "defaultSelectNum": 1,
                  "unitPerStep": 1,
                  "exchange": false,
                  "hide": false,
                  "rank": 3,
                  "ruleType": 20,
                  "multiChoice": false,
                  "groupMultiChoice": false,
                  "price": "0",
                  "premiumName": "少少甜"
                },
                {
                  "premiumId": "2559321363",
                  "premiumGroupCode": "18",
                  "defaultSelect": false,
                  "mustSelect": false,
                  "maxChoice": 1,
                  "minChoice": 0,
                  "maxFreeNum": 0,
                  "defaultSelectNum": 1,
                  "unitPerStep": 1,
                  "exchange": false,
                  "hide": false,
                  "rank": 4,
                  "ruleType": 20,
                  "multiChoice": false,
                  "groupMultiChoice": false,
                  "price": "0",
                  "premiumName": "微甜"
                },
                {
                  "premiumId": "2559351882",
                  "premiumGroupCode": "18",
                  "defaultSelect": true,
                  "mustSelect": false,
                  "maxChoice": 1,
                  "minChoice": 0,
                  "maxFreeNum": 0,
                  "defaultSelectNum": 1,
                  "unitPerStep": 1,
                  "exchange": false,
                  "hide": false,
                  "rank": 5,
                  "ruleType": 20,
                  "multiChoice": false,
                  "groupMultiChoice": false,
                  "price": "0",
                  "premiumName": "不另外加糖"
                }
              ]
            },
            {
              "skuId": "2878676655",
              "spuId": "2304702978",
              "skuName": "超大杯",
              "isAvailable": true,
              "currentPrice": "3800",
              "originalPrice": "3800",
              "addPrice": "3800",
              "stockCount": -1,
              "mopSkuSaleAttrList": [
                {
                  "groupCode": "64",
                  "attributeId": "2496648394"
                }
              ],
              "mopCustomRuleList": [
                {
                  "premiumGroupCode": "17",
                  "defaultSelect": true,
                  "mustSelect": true,
                  "maxChoice": 1,
                  "minChoice": 1,
                  "defaultSelectNum": 1,
                  "unitPerStep": 1,
                  "exchange": false,
                  "hide": false,
                  "fold": false,
                  "rank": 1,
                  "ruleType": 10,
                  "multiChoice": false,
                  "groupMultiChoice": false
                },
                {
                  "premiumGroupCode": "50",
                  "defaultSelect": true,
                  "mustSelect": true,
                  "maxChoice": 1,
                  "minChoice": 1,
                  "defaultSelectNum": 1,
                  "unitPerStep": 1,
                  "exchange": false,
                  "hide": false,
                  "fold": false,
                  "rank": 2,
                  "ruleType": 10,
                  "multiChoice": false,
                  "groupMultiChoice": false
                },
                {
                  "premiumGroupCode": "113",
                  "defaultSelect": true,
                  "mustSelect": true,
                  "maxChoice": 1,
                  "minChoice": 1,
                  "defaultSelectNum": 1,
                  "unitPerStep": 1,
                  "exchange": false,
                  "hide": false,
                  "fold": false,
                  "rank": 3,
                  "ruleType": 10,
                  "multiChoice": false,
                  "groupMultiChoice": false
                },
                {
                  "premiumGroupCode": "18",
                  "defaultSelect": true,
                  "mustSelect": true,
                  "maxChoice": 1,
                  "minChoice": 1,
                  "defaultSelectNum": 1,
                  "unitPerStep": 1,
                  "exchange": false,
                  "hide": false,
                  "fold": false,
                  "rank": 4,
                  "ruleType": 10,
                  "multiChoice": false,
                  "groupMultiChoice": false
                },
                {
                  "premiumId": "2559347768",
                  "premiumGroupCode": "17",
                  "defaultSelect": true,
                  "mustSelect": false,
                  "maxChoice": 1,
                  "minChoice": 0,
                  "maxFreeNum": 0,
                  "defaultSelectNum": 1,
                  "unitPerStep": 1,
                  "exchange": false,
                  "hide": false,
                  "rank": 1,
                  "ruleType": 20,
                  "multiChoice": false,
                  "groupMultiChoice": false,
                  "price": "0",
                  "premiumName": "冰"
                },
                {
                  "premiumId": "2559404566",
                  "premiumGroupCode": "50",
                  "defaultSelect": true,
                  "mustSelect": false,
                  "maxChoice": 1,
                  "minChoice": 0,
                  "maxFreeNum": 0,
                  "defaultSelectNum": 1,
                  "unitPerStep": 1,
                  "exchange": false,
                  "hide": false,
                  "rank": 1,
                  "ruleType": 20,
                  "multiChoice": false,
                  "groupMultiChoice": false,
                  "price": "0",
                  "premiumName": "意式拼配"
                },
                {
                  "premiumId": "2559402655",
                  "premiumGroupCode": "113",
                  "defaultSelect": true,
                  "mustSelect": false,
                  "maxChoice": 1,
                  "minChoice": 0,
                  "maxFreeNum": 0,
                  "defaultSelectNum": 1,
                  "unitPerStep": 1,
                  "exchange": false,
                  "hide": false,
                  "rank": 1,
                  "ruleType": 20,
                  "multiChoice": false,
                  "groupMultiChoice": false,
                  "price": "0",
                  "premiumName": "默认浓度"
                },
                {
                  "premiumId": "2559361699",
                  "premiumGroupCode": "18",
                  "defaultSelect": false,
                  "mustSelect": false,
                  "maxChoice": 1,
                  "minChoice": 0,
                  "maxFreeNum": 0,
                  "defaultSelectNum": 1,
                  "unitPerStep": 1,
                  "exchange": false,
                  "hide": false,
                  "rank": 1,
                  "ruleType": 20,
                  "multiChoice": false,
                  "groupMultiChoice": false,
                  "price": "0",
                  "premiumName": "标准甜"
                },
                {
                  "premiumId": "2559380099",
                  "premiumGroupCode": "50",
                  "defaultSelect": false,
                  "mustSelect": false,
                  "maxChoice": 1,
                  "minChoice": 0,
                  "maxFreeNum": 0,
                  "defaultSelectNum": 1,
                  "unitPerStep": 1,
                  "exchange": false,
                  "hide": false,
                  "rank": 2,
                  "ruleType": 20,
                  "multiChoice": false,
                  "groupMultiChoice": false,
                  "price": "0",
                  "premiumName": "深烘拼配"
                },
                {
                  "premiumId": "2559341294",
                  "premiumGroupCode": "113",
                  "defaultSelect": false,
                  "mustSelect": false,
                  "maxChoice": 1,
                  "minChoice": 0,
                  "maxFreeNum": 0,
                  "defaultSelectNum": 1,
                  "unitPerStep": 1,
                  "exchange": false,
                  "hide": false,
                  "rank": 2,
                  "ruleType": 20,
                  "multiChoice": false,
                  "groupMultiChoice": false,
                  "price": "300",
                  "premiumName": "加单份浓缩"
                },
                {
                  "premiumId": "2559306598",
                  "premiumGroupCode": "18",
                  "defaultSelect": false,
                  "mustSelect": false,
                  "maxChoice": 1,
                  "minChoice": 0,
                  "maxFreeNum": 0,
                  "defaultSelectNum": 1,
                  "unitPerStep": 1,
                  "exchange": false,
                  "hide": false,
                  "rank": 2,
                  "ruleType": 20,
                  "multiChoice": false,
                  "groupMultiChoice": false,
                  "price": "0",
                  "premiumName": "少甜"
                },
                {
                  "premiumId": "2559371693",
                  "premiumGroupCode": "50",
                  "defaultSelect": false,
                  "mustSelect": false,
                  "maxChoice": 1,
                  "minChoice": 0,
                  "maxFreeNum": 0,
                  "defaultSelectNum": 1,
                  "unitPerStep": 1,
                  "exchange": false,
                  "hide": false,
                  "rank": 3,
                  "ruleType": 20,
                  "multiChoice": false,
                  "groupMultiChoice": false,
                  "price": "0",
                  "premiumName": "埃塞金烘"
                },
                {
                  "premiumId": "2559346070",
                  "premiumGroupCode": "18",
                  "defaultSelect": false,
                  "mustSelect": false,
                  "maxChoice": 1,
                  "minChoice": 0,
                  "maxFreeNum": 0,
                  "defaultSelectNum": 1,
                  "unitPerStep": 1,
                  "exchange": false,
                  "hide": false,
                  "rank": 3,
                  "ruleType": 20,
                  "multiChoice": false,
                  "groupMultiChoice": false,
                  "price": "0",
                  "premiumName": "少少甜"
                },
                {
                  "premiumId": "2559321363",
                  "premiumGroupCode": "18",
                  "defaultSelect": false,
                  "mustSelect": false,
                  "maxChoice": 1,
                  "minChoice": 0,
                  "maxFreeNum": 0,
                  "defaultSelectNum": 1,
                  "unitPerStep": 1,
                  "exchange": false,
                  "hide": false,
                  "rank": 4,
                  "ruleType": 20,
                  "multiChoice": false,
                  "groupMultiChoice": false,
                  "price": "0",
                  "premiumName": "微甜"
                },
                {
                  "premiumId": "2559351882",
                  "premiumGroupCode": "18",
                  "defaultSelect": true,
                  "mustSelect": false,
                  "maxChoice": 1,
                  "minChoice": 0,
                  "maxFreeNum": 0,
                  "defaultSelectNum": 1,
                  "unitPerStep": 1,
                  "exchange": false,
                  "hide": false,
                  "rank": 5,
                  "ruleType": 20,
                  "multiChoice": false,
                  "groupMultiChoice": false,
                  "price": "0",
                  "premiumName": "不另外加糖"
                }
              ]
            }
          ],
          "mopProductAttrGroups": [
            {
              "groupName": "杯型",
              "groupCode": "64",
              "maxChoiceNum": 1,
              "minChoiceNum": 1,
              "isSellAttributeGroup": true,
              "rank": 1,
              "mopProductAttrItems": [
                {
                  "attrId": "2497190611",
                  "attrValue": "大杯",
                  "rank": 1,
                  "attrAddPrice": "0"
                },
                {
                  "attrId": "2496648394",
                  "attrValue": "超大杯 ¥3",
                  "rank": 2,
                  "attrAddPrice": "0"
                }
              ]
            },
            {
              "groupName": "温度",
              "groupCode": "17",
              "maxChoiceNum": 1,
              "minChoiceNum": 1,
              "isSellAttributeGroup": false,
              "multiChoice": false,
              "chooseMultiPremium": false,
              "rank": 1,
              "mopProductAttrItems": [
                {
                  "attrId": "2559347768",
                  "attrValue": "冰",
                  "rank": 1,
                  "attrAddPrice": "0.00"
                }
              ]
            },
            {
              "groupName": "咖啡豆",
              "groupCode": "50",
              "maxChoiceNum": 1,
              "minChoiceNum": 1,
              "isSellAttributeGroup": false,
              "multiChoice": false,
              "chooseMultiPremium": false,
              "rank": 2,
              "mopProductAttrItems": [
                {
                  "attrId": "2559404566",
                  "attrValue": "意式拼配",
                  "rank": 1,
                  "attrAddPrice": "0.00"
                },
                {
                  "attrId": "2559380099",
                  "attrValue": "深烘拼配",
                  "rank": 2,
                  "attrAddPrice": "0.00"
                },
                {
                  "attrId": "2559371693",
                  "attrValue": "埃塞金烘",
                  "rank": 3,
                  "attrAddPrice": "0.00"
                }
              ]
            },
            {
              "groupName": "咖啡浓度",
              "groupCode": "113",
              "maxChoiceNum": 1,
              "minChoiceNum": 1,
              "isSellAttributeGroup": false,
              "multiChoice": false,
              "chooseMultiPremium": false,
              "rank": 3,
              "mopProductAttrItems": [
                {
                  "attrId": "2559402655",
                  "attrValue": "默认浓度",
                  "rank": 1,
                  "attrAddPrice": "0.00"
                },
                {
                  "attrId": "2559341294",
                  "attrValue": "加单份浓缩",
                  "rank": 2,
                  "attrAddPrice": "300.00"
                }
              ]
            },
            {
              "groupName": "糖度",
              "groupCode": "18",
              "maxChoiceNum": 1,
              "minChoiceNum": 1,
              "isSellAttributeGroup": false,
              "multiChoice": false,
              "chooseMultiPremium": false,
              "rank": 4,
              "mopProductAttrItems": [
                {
                  "attrId": "2559361699",
                  "attrValue": "标准甜",
                  "rank": 1,
                  "attrAddPrice": "0.00"
                },
                {
                  "attrId": "2559306598",
                  "attrValue": "少甜",
                  "rank": 2,
                  "attrAddPrice": "0.00"
                },
                {
                  "attrId": "2559346070",
                  "attrValue": "少少甜",
                  "rank": 3,
                  "attrAddPrice": "0.00"
                },
                {
                  "attrId": "2559321363",
                  "attrValue": "微甜",
                  "rank": 4,
                  "attrAddPrice": "0.00"
                },
                {
                  "attrId": "2559351882",
                  "attrValue": "不另外加糖",
                  "rank": 5,
                  "attrAddPrice": "0.00"
                }
              ]
            }
          ],
          "extendInfoMap": {}
        }
      },
      "isSupport": true,
      "skuUpperLimit": 15
    },
    "mopProductPriceVO": {
      "currentPrice": "3500",
      "mopCurrentPrice": "3500",
      "dealCurrentPrice": "0",
      "totalPrice": "3500",
      "selectNum": 1,
      "dealTotalPrice": "0",
      "dealDiscountPrice": "0",
      "dealSelectNum": 0,
      "dealSalePrice": "0",
      "tips": [],
      "needQi": true
    },
    "prepareTimeText": "现在下单，最快6分钟到店取餐"
  }
}
```

### PROMPT

```
// 代码块
客制化目标接口 <https://apimobile.meituan.com/mop/api/menu/productDetailForPoiShelf> 返回的结构在/Users/ceilf6/Desktop/ka-skills-mop-order-response/productDetailForPoiShelf.json
[$karpathy-guidelines](/Users/ceilf6/.codex/skills/karpathy-guidelines/SKILL.md) 查看后评估能否通过复用其他type商品的客制化逻辑实现最小变更
```

### Plan

```
// 代码块
# 联名套餐逐杯客制化最小变更计划

## Summary
- `comboDishGroupList` 已提供联名子商品的 `spuId`、`skuIdList`、`defaultChooseSku` 和默认 `premiumList`，但只够默认下单。
- `productDetailForPoiShelf.json` 与普通 type=10 结构一致，包含 `mopProductAttrGroups` 和 `mopSkuList[].mopCustomRuleList`，可复用现有 `parseProduct` + `resolveNonSaleAttrs`。
- 第一版按“选择顺序”逐杯客制化：例如第 1 个联名子商品用第 1 组客制化参数，第 2 个联名子商品用第 2 组。

## Key Changes
- 新增 `productDetailForPoiShelf` API 调用与解析：
  - 输入使用 combo 子商品中的 `spuId`、默认/指定 `skuId`，以及当前 `poiId`、`dealId`、登录态公共参数。
  - 解析结果复用现有普通商品结构：`spuId`、`spuName`、`defaultSkuId`、`skuList`、`attrGroups`、`customRules`。
  - 若接口请求字段推断不对，只调整该 API 请求构造，不改下单结构。

- 扩展联名套餐参数：
  - 保留 `--combo-spu` / `--combo-sku`。
  - 新增按选择顺序的 `--combo-attr <index:groupName:value>`，可多次传。
  - 示例：`--combo-spu 2229314904 --combo-spu 2304702978 --combo-attr 1:温度:冰 --combo-attr 1:糖度:少甜 --combo-attr 2:糖度:微甜`。
  - index 从 1 开始，对应最终选中的联名子商品顺序；未指定的杯继续使用 `defaultChooseSku.premiumList`。

- 修改 type=30 构单：
  - `selectDishComboItems` 仍负责选中子商品和补齐必选组。
  - 对 `canCustomization=true` 且存在对应 `--combo-attr` 的子商品，调用 `productDetailForPoiShelf` 获取详情。
  - 用详情中的 `attrGroups` 调 `resolveNonSaleAttrs`，替换该杯 `mopPremiumItemList`。
  - `itemKey` 继续使用现有 `buildDishComboChildItemKey(groupId, spuId, skuId, premiumList)`，确保 premium 变更反映到 key。
  - `order` 和 `submit` 全流程都使用同一套 type=30 构造函数，避免两边行为漂移。

- 更新输出与文档：
  - `deal` 输出中对 `canCustomization=true` 的联名饮品提示可用 `--combo-attr`。
  - skill 文档移除“只能默认值下单”的绝对限制，改为“支持逐杯客制化；未指定则默认值”。

## Test Plan
- 用 `productDetailForPoiShelf.json` 验证解析：
  - `spuId=2304702978`
  - `attrGroups` 含杯型、温度、咖啡豆、咖啡浓度、糖度
  - `resolveNonSaleAttrs(..., ["糖度:微甜"])` 生成 `premiumId=2559321363`

- 用联名 combo fixture 验证：
  - 默认不传 `--combo-attr` 时，请求体仍使用 `defaultChooseSku.premiumList`
  - 传 `--combo-attr 1:糖度:微甜` 后，第 1 杯 `mopPremiumItemList` 替换为对应 premium
  - verbose 请求体包含更新后的 `mopComboDishItem.mopComboSkuItemList[].mopPremiumItemList`
  - `itemKey` 中 premium 片段同步变化
  - 周边等 `canCustomization=false` 商品传 `--combo-attr` 时给出明确错误

- 跑：
  - `pnpm --dir cli/mop/mop-order run typecheck`
  - `pnpm --dir cli/mop/mop-order run build:clean`
  - `TEST_AUTH_STATE=logged_out pnpm --dir cli/mop/mop-order run test:cases`

## Assumptions
- `productDetailForPoiShelf` 的请求可由 combo 子商品字段加当前门店/登录态参数构造；如果真实接口要求额外字段，需要补一份请求抓包，只改 API 请求层。
- 逐杯客制化按最终选择顺序绑定，index 从 1 开始。
- 不复用 type=10/20 的整段 purchaseItem 构造，只复用商品详情解析和非售卖属性解析，避免破坏 type=30 的 `mopComboDishItem` 协议。
```

### 执行

```
// 代码块
已实现联名套餐逐杯客制化，走最小复用路径：不复用 type=10/20 的整段下单协议，只复用商品详情解析和非售卖属性解析。

主要改动：

- 新增 [product.ts](/Users/ceilf6/Desktop/ka-skills/cli/mop/mop-order/src/api/product.ts)：调用/解析 `productDetailForPoiShelf`，用普通商品结构补齐联名子商品的 `attrGroups`。
- [order.ts](/Users/ceilf6/Desktop/ka-skills/cli/mop/mop-order/src/command/order.ts) / [submit.ts](/Users/ceilf6/Desktop/ka-skills/cli/mop/mop-order/src/command/submit.ts)：新增 `--combo-attr <index:groupName:value>`，按最终选择顺序逐杯应用，例如 `--combo-attr 2:糖度:微甜`。
- type=30 构单会在有 `--combo-attr` 时补查对应子商品详情，并替换该杯 `mopPremiumItemList` 和 `itemKey`；未指定的维度保留 combo 默认 premium。
- 周边这类 `canCustomization=false` 的子商品如果传 `--combo-attr`，会明确报错。
- 版本已 bump 到 `@meishi/food-mop-order@0.4.6`，因为你已经发布了 `0.4.5`。

验证已跑：

- `pnpm --dir cli/mop/mop-order run typecheck`
- `pnpm --dir cli/mop/mop-order run build:clean`
- `TEST_AUTH_STATE=logged_out pnpm --dir cli/mop/mop-order run test:cases`：6 通过，0 失败，2 跳过
- `npm pack --dry-run --json`：产物为 `@meishi/food-mop-order@0.4.6`
- 离线 fixture 验证：`糖度:微甜` 正确生成 `premiumId=2559321363`，并同步进入第二杯 `itemKey`

注意：`productDetailForPoiShelf` 的请求体是按当前样例和 combo 字段推断的。如果真实接口要求额外抓包字段，后续只需要调整 [config.ts](/Users/ceilf6/Desktop/ka-skills/cli/mop/mop-order/src/config.ts) 里的请求构造，不需要推翻 type=30 下单结构。
```

### 提交请求兼容

```
// 代码块
你这次的新信息说明：**上次“请求 productDetailForPoiShelf”这条路不是错的，也不是多此一举**。真正漏的是后半段 submit 请求体没有完全对齐 App 抓包结构。

我已按你提供的 [submit.json](/Users/ceilf6/Desktop/ka-skills-mop-order-response/submit.json) 修了两个关键差异：

- `mopComboDishItem.itemKey` 不再传裸 `comboSkuId`，改成真实抓包形态：`外层 deal itemKey + "-" + comboSkuId`
- `userSelectedDealItem.mopDishComboItem.currSelectedList[].userCustomizationList` 现在会回填逐杯 `chooseSku.skuId + premiumList`，不再是空数组
- 同时保留子商品原始 `media`，并移除 type=30 子项里抓包没有的 `isSupplementSku`

我也补了 troubleshooting，不再把“无法获取联名套餐子商品客制化规格”简单归因成 CLI 限制，而是明确让用户用 `--verbose` 定位 `productDetailForPoiShelf` 返回是否为空。

验证已跑过：

- `pnpm --dir cli/mop/mop-order run typecheck`
- `pnpm --dir cli/mop/mop-order run build:clean`
- `TEST_AUTH_STATE=logged_out pnpm --dir cli/mop/mop-order run test:cases`：6 通过，0 失败，2 跳过
- `npm pack --dry-run --json`：当前包为 `@meishi/food-mop-order@0.4.6`

注意：如果你已经把上一版 `0.4.6` 发出去了，这次修复发布前需要 bump 到 `0.4.7`，否则 npm registry 会拒绝重复版本。
```

## 成功跑通

> 注意，login 后没有 uuid 也是能跑的，如果这里被阻塞的话检查一下是不是不在**内网**（我经常为了压缩codex上下文所以用自己梯子，忘记切回来导致被阻塞）
> 

### 瑞幸

测试用例

```
// 代码块
/new
```

```
// 代码块
你的 food-mop-order 版本是多少？
```

```
// 代码块
我要喝瑞幸咖啡
```

```
// 代码块
还是这家店，我要喝【吧唧·蛋仔派对联名】双杯套餐，并且我要客制化
```

```
// 代码块
第一杯陨石拿铁支持哪些客制化？
```

```
// 代码块
我要超大杯、埃塞金烘、加单份浓缩、少少甜
```

```
// 代码块
第二杯我要橙C美式，默认即可
```

[image.png](https://km.sankuai.com/api/file/cdn/2759161502/234490462232?contentType=1&isNewContent=false)

[image.png](https://km.sankuai.com/api/file/cdn/2759161502/234494292372?contentType=1&isNewContent=false)

[image.png](https://km.sankuai.com/api/file/cdn/2759161502/234499209685?contentType=1&isNewContent=false)

[image.png](https://km.sankuai.com/api/file/cdn/2759161502/234499292197?contentType=1&isNewContent=false)

[image.png](https://km.sankuai.com/api/file/cdn/2759161502/234495265911?contentType=1&isNewContent=false)

TODO: 请求接口返回的是大杯情况下支持的客制化信息，超大杯支持的信息不一定符合，像一般在**超大杯**情况下是不支持热的（skuID）

现在已经打通了MVP

[image.png](https://km.sankuai.com/api/file/cdn/2759161502/234521423964?contentType=1&isNewContent=false)

[image.png](https://km.sankuai.com/api/file/cdn/2759161502/234528661693?contentType=1&isNewContent=false)

[ef7508ff-5705-4eeb-b717-757a0b2effc3.jpeg](https://km.sankuai.com/api/file/cdn/2759161502/234524305420?contentType=1&isNewContent=false)

### 汉堡王

[image.png](https://km.sankuai.com/api/file/cdn/2759161502/234535256608?contentType=1&isNewContent=false)

从 appmock 中拿到店面 poiId

测试用例

```
// 代码块
我要点poiId为 1101125638 的店
```

```
// 代码块
我要联名套餐
```

```
// 代码块
我要双人分享
```

```
// 代码块
来一个【双人餐】欢乐桶6件套
```

```
// 代码块
我要双层牛肉芝士堡，KING暴风阿华田 和 薯霸王，两杯雪碧
```

```
// 代码块
那就薯霸王吧
```

[image.png](https://km.sankuai.com/api/file/cdn/2759161502/234531161798?contentType=1&isNewContent=false)

[image.png](https://km.sankuai.com/api/file/cdn/2759161502/234529613496?contentType=1&isNewContent=false)

[image.png](https://km.sankuai.com/api/file/cdn/2759161502/234532873213?contentType=1&isNewContent=false)