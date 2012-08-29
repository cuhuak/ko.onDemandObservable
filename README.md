ko.onDemandObservable
=====================

- ko.onDemandObservable
- ko.onDemandObservableArray

##Example

    function Tab(id, name) {
        this.id = id;
        this.name = ko.observable(name);
        //sample of using an on-demand observable here
        this.details = ko.onDemandObservable(this.getDetails, this);
    }

    Tab.prototype.getDetails = function() {
        $.ajax({
            type: 'POST',
            url: '/echo/json/',
            data: {
                json: ko.toJSON({
                    details: new Date().toLocaleTimeString() + " " + this.name() + fakeText
                }),
                delay: 1
            },
            context: this,
            success: function(data) {
                this.details(data.details);
            },
            dataType: 'json'
        });
    };
