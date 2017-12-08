#include<iostream>
using namespace std;
class Date
{
private:
	int _year;
	int _month;
	int _day;
public:
	Date(int year = 1990, int month = 1, int day = 1)
		:_year(year)
		, _month(month)
		, _day(day)
	{
		if (!
			(year >= 1990 &&
			(month > 0 && month<13) &&
			day>0 && GetMonthdays(year, month))
			)
		{
			_year = 1990;
			_month = 1;
			_day = 1;
		}
	}
	Date operator+(int days)
	{
		if (days<0)
			return *this - (0 - days);
		Date temp(*this);
		temp._day += days;
		int daysInMOnth = 0;
		if (temp._day > (daysInMOnth = GetMonthdays(temp._year, temp._month)))
		{
			temp._day -= daysInMOnth;
			temp._month++;
			if (temp._month > 12)
			{
				temp._year++;
				temp._month = 1;
			}
		}
		return temp;
	}
	Date operator-(int days)
	{
		if (days>0)
			return *this - (0 - days);
		Date temp(*this);
		temp._day -= days;
		if (temp._day <= 0)
		{
			temp._month--;
			if (temp._month == 0)
			{
				temp._year--;
				temp._month = 12;
			}
			temp._day += GetMonthdays(temp._year, temp._month);
		}
		return temp;
	}
	int operator-(const Date d)
	{
		Date maxDate(*this);
		Date minDate(d);
		if (maxDate < minDate)
		{
			minDate = *this;
			maxDate = d;
		}
		int count = 0;
		while (minDate != maxDate)
		{
			count++;
			minDate++;
		}
		return count;
	}
	bool operator<(const Date d)
	{
		if (_year>d._year ||
			_year == d._year&&_month > d._month ||
			_year == d._year&&_month == d._month&&_day > d._day)
			return true;
		else return false;
	}
	Date& operator++()
	{
		*this = *this + 1;
		return *this;
	}
	Date operator++(int)
	{
		/*  
		Date temp(*this);
		_day += 1;
		if (_day > GetMonthdays(_year, _month))
		{
			_month += 1;
			if (_month > 12)
				_year += 1;
			_day = 1;
		}
		return temp;
		*/
		Date temp(*this);
		*this = *this + 1;
		return temp;
	}
	Date& operator--()
	{
		*this = *this - 1;
		return *this;

	}
	Date operator--(int)
	{
		Date temp(*this);
		*this = *this - 1;
		return temp;
	}
	bool operator==(const Date& d)
	{
		return _year == d._year&&_month == d._month&&_day == d._day;
	}

	bool operator!=(const Date& d)
	{
		/*
		if (_year == d._year&&_month == d._month&&_day ==d._day)
			return false;
		else return true;  
		*/
		return !((*this) == d);
	}
	friend ostream& operator<<(ostream& _cout, const Date& d)
	{
		_cout << d._year << "-" << d._month << "-" << d._day;
		return _cout;
	}
	int GetMonthdays(int year, int month)
	{
		int Month[] = { 0, 31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31 };
		if (month == 2)
		{
			if ((year % 4 == 0 && year % 100 != 0) || year % 400 == 0)
				return Month[month] + 1;
		}
		return Month[month];
	}
};
int main(void)
{
	Date d1(2017, 11, 16);
	cout << d1 << endl;
	Date d2;
	d2 = d1 + 100;
	cout << d2 << endl;
	d2 = d1 - 500;
	cout << d2 << endl;
}
