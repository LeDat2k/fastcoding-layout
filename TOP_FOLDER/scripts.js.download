var app = app || {};

var spBreak = 767.98;
var offsetY;

app.init = function () {
  app.navigationMobile();
  app.slider();
  app.accordion();
  app.tabletViewport();
  app.sliderKeyVisual();
  app.tabs();
  app.listTabs();
  app.quantityValue();
  app.detectDevice();
};

app.isMobile = function () {
  return window.matchMedia('(max-width: ' + spBreak + 'px)').matches;
};

app.quantityValue = function () {
  if ($('.js-handle-quantity').length) {
    var inputQuantity = $('.js-handle-quantity .input-count');
    var numberValueInit = parseInt(inputQuantity.val(), 10);
    if (numberValueInit <= 1) {
      $('.js-handle-quantity .reduce').addClass('is-disabled');
    }

    $('.js-handle-quantity .increase').click(function () {
      var numberValue = parseInt(inputQuantity.val(), 10);
      numberValue++;
      inputQuantity.val(numberValue);
      if (numberValue > 1) {
        $('.js-handle-quantity .reduce').removeClass('is-disabled');
      }
    });

    $('.js-handle-quantity .reduce').click(function () {
      var numberValue = parseInt(inputQuantity.val(), 10);
      numberValue--;
      inputQuantity.val(numberValue);
      if (numberValue <= 1) {
        $('.js-handle-quantity .reduce').addClass('is-disabled');
      }
    });

    inputQuantity.on('change', function () {
      if ($(this).val() <= 1) {
        $('.js-handle-quantity .reduce').addClass('is-disabled');
      } else {
        $('.js-handle-quantity .reduce').removeClass('is-disabled');
      }
      if ($(this).val() < 1) {
        inputQuantity.val(1);
      }
    });
  }
};

app.slider = function () {
  if ($('.js-slider-testimonial').length) {
    $('.js-slider-testimonial').slick({
      dots: true,
      infinite: true,
      speed: 1000,
      fade: true,
      arrows: false,
      autoplay: true,
      slidesToShow: 1,
      adaptiveHeight: true
    });
  }
};

app.closeMenu = function () {
  $('body').css({
    position: 'static',
    top: 'auto'
  });
  $(window).scrollTop(offsetY);
};

app.navigationMobile = function () {
  var navigation = $('.js-navigation');
  $('.js-button-menu').click(function () {
    $('header').toggleClass('is-active');
    navigation.addClass('is-show');
    $(this).toggleClass('is-active');
    if ($(this).hasClass('is-active')) {
      offsetY = window.pageYOffset;
      $('body').css({
        position: 'fixed',
        top: -offsetY + 'px',
        width: '100%'
      });
      $('.js-overlay').addClass('is-show');
      navigation.stop().fadeIn();
    } else {
      app.closeMenu();
      navigation.removeClass('is-show');
      navigation.stop().fadeOut();
      $('.js-overlay').removeClass('is-show');
    }
    return false;
  });
  $('.js-overlay').click(function () {
    $('.js-overlay').removeClass('is-show');
    navigation.stop().fadeOut();
    app.closeMenu();
    $('.js-button-menu').removeClass('is-active');
  });
};

app.tabletViewport = function () {
  var viewport = document.getElementById('viewport');

  var viewportSet = function () {
    if (screen.width >= 768 && screen.width <= 1240) {
      viewport.setAttribute('content', 'width=1336, user-scalable=0');
      $('html').addClass('is-tablet');
    } else {
      viewport.setAttribute(
        'content',
        'width=device-width, initial-scale=1, shrink-to-fit=no, user-scalable=0'
      );
      $('html').removeClass('is-tablet');
    }
  };

  viewportSet();

  window.onload = function () {
    viewportSet();
  };

  window.onresize = function () {
    viewportSet();
  };
};

app.accordion = function () {
  $('.js-accordion')
    .find('.js-accordion-heading')
    .click(function () {
      $(this)
        .parent()
        .stop()
        .toggleClass('is-active');
      $(this)
        .parent()
        .find('.js-accordion-content')
        .stop()
        .eq(0)
        .slideToggle(300);
    });
};

app.sliderKeyVisual = function () {
  if ($('.js-slider-keyvisual').length) {
    $('.js-slider-keyvisual').slick({
      slidesToShow: 1,
      slidesToScroll: 1,
      arrows: false,
      fade: true,
      autoplay: true,
      autoplaySpeed: 4000,
      speed: 1000,
      dots: false,
      asNavFor: '.js-slider-thumbnail'
    });

    $('.js-slider-thumbnail').slick({
      slidesToShow: 8,
      slidesToScroll: 1,
      arrows: false,
      autoplay: false,
      infinite: false,
      dots: false,
      focusOnSelect: true,
      row: 1,
      asNavFor: '.js-slider-keyvisual'
    });
  }
};

app.tabs = function () {
  $('.js-tabs li').click(function () {
    var dataTab = $(this).attr('data-tab');
    $('.js-tabs li').removeClass('is-current');
    $('.js-tab-content .tab-content').removeClass('is-current');
    $(this).addClass('is-current');
    $('#' + dataTab).addClass('is-current');
  });
};

app.listTabs = function () {
  if ($('.js-list-tabs').length) {
    var selector = '.js-list-tabs li',
      selectorContent = '.tab-container';
    var init = function () {
      $(selector).click(function () {
        var tabId = $(this).attr('data-tab');
        $(selector).removeClass('is-current');
        $(selectorContent).removeClass('is-current');
        $(this).addClass('is-current');
        $('#' + tabId).addClass('is-current');
      });
    };
    if ($(selector).length) {
      init();
    }
  }
};

app.detectDevice = function () {
  var userAgent = navigator.userAgent.toLowerCase();

  // System
  if (userAgent.indexOf('mac os x') != -1) {
    $('html').addClass('is-ios');
  }
  if (userAgent.indexOf('android') > -1) {
    $('html').addClass('is-android');
  }

  //Browser
  if (userAgent.indexOf('chrome') > -1) {
    $('html').addClass('is-chrome');
  }
  if (userAgent.indexOf('trident') > -1) {
    $('html').addClass('is-ie');
  }
  if (userAgent.indexOf('edge') > -1) {
    $('html').removeClass('is-chrome');
    $('html').addClass('is-edge');
  }
  if (userAgent.indexOf('edg/') > -1) {
    $('html').removeClass('is-chrome');
    $('html').addClass('is-chromium');
  }
  if (userAgent.indexOf('firefox') > -1) {
    $('html').addClass('is-firefox');
  }
  if (userAgent.indexOf('safari') > -1 && userAgent.indexOf('chrome') < 0) {
    $('html').addClass('is-safari');
  }
};

$(function () {
  app.init();
});
